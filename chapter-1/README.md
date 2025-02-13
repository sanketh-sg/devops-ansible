Ansible can be setup without Vagrant in production we may not use Vagrant at all.
In such case, Add the ssh keys to the ansible controller and when runnning ansible cmd we provide ~/.ssh/ansible

package is a generic package manager

- Targetting specific node

 use --limit to limit the cmds to specfic server

 pre_tasks option in ansible playbook is used to run the any tasks before the play runs.

 tags adds metadata to plays
 --tags can also be used to target servers

# managing files
 copy: copies a file to server
 takes src, dest, owner, group, mode as parameters

 we can also install packages from remote sources by using url and enabling option remote_src:yes

# Managing Services
services: takes name,state,enabled as parameters