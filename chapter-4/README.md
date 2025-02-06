*Ansible playbooks*

Ansible config files, contains list of tasks that will be run against a server or group of servers.

The greater-than sign (>) immediately following the command: module directive tells YAML “automatically quote the next set of indented lines as one long string, with each line separated by a space”. 

One thing that is universal to all of Ansible’s SSH connection methods is that Ansible
uses the connection to transfer one or a few files defining a play or command to the
remote server, then runs the play/command, then deletes the transferred file(s), and
reports back the results.
