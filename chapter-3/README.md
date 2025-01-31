We’re going to manage three VMs: two app servers and a database server. Many simple web applications and websites have a similar architecture.

I am using the docker images method here to get the image instead of building it using a docker file lik in prev chapters
(has some issues with ssh need to figure out how re create)

I have set up a custom network in docker as docker provider does not support private network as in vbox

```console
- docker network create --subnet 192.168.3.0/24 nw-ansi
```
in Ansible group the servers into app and db which are merged to form a thord group called 'multi' and we run ansible cmds on this group.

ansible multi -a ping
ansible multi -a "df -h"
ansible multi -a "date"

Setting up allpications servers

```bash
- ansible app -b -m apt -a "update_cache=yes"  # Ensure package lists are updated
- ansible app -b -m apt -a "name=python3-mysqldb state=present"
- ansible- app -b -m apt -a "name=python3-setuptools state=present"
- ansible app -b -m apt -a "name=python3-pip state=present"
- ansible app -b -m pip -a "name=django"
- ansible app -a "python3 -c 'import django; print(django.get_version())'"
```

Setting up DB

```bash
ansible db -b -m apt -a "name=mariadb-server state=present"
ansible db -b -m service -a "name=mariadb state=started enabled=yes"
ansible db -b -m apt -a "name=ufw state=present"
ansible db -b -a "ufw --force reset"
ansible db -b -m ufw -a "rule=allow proto=tcp from=192.168.60.0/24 to=any port=3306"
ALTER USER 'root'@'localhost' IDENTIFIED VIA mysql_native_password USING PASSWORD('db-root');
ansible db -b -m mysql_user -a "name=django host=% password=12345 priv=*.*:ALL state=present login_user=root login_password=db-root"
```
--limit to filter single servers
-m file  to create files and dictionaries

Ansible’s Accelerated mode achieves greater performance for playbooks. Instead of connecting repeatedly via SSH, Ansible connects via SSH initially,then uses the AES key used in the initial connection to communicate further commands and transfers via a separate port (5099 by default, but this is configurable) enable it  by accelerate: true