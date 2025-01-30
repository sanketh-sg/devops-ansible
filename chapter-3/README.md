We’re going to manage three VMs: two app servers and a database server. Many simple web applications and websites have a similar architecture.

I am using the docker images method here to get the image instead of building it using a docker file lik in prev chapters

I have set up a custom network in docker as docker provider does not support private network as in vbox

```console
- docker network create --subnet 192.168.3.0/24 nw-ansi
```
