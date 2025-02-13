# User management and Roles
In order to make playbooks better readable we can roles and assign them to hosts

For roles to work we need to do some file management, it requires a seperate folder called roles and inside roles we create seperate folder for each role we define in playbook.

Each role will have folders based on the tasks that are performed.
it containes tasks to define tasks that the role should perform
also files folder to keep the files the tasks require 

```sh
.
├── Vagrantfile
├── ansible.cfg
├── app1
│   └── Dockerfile
├── app2
│   └── Dockerfile
├── hosts.ini
├── playbook.yml
└── roles
    ├── base
    │   └── tasks
    │       └── main.yml
    ├── db_server
    │   └── tasks
    │       └── main.yml
    └── web_server
        ├── files
        │   └── default_site.html
        └── tasks
            └── main.yml
```

Host variables
Lets say we have servers running different OS, Normally we need to set up different tasks for each OS type. Which includes redundant code. THis can be solved by using host variables.

setup a folder host_vars which contains files named after each host(name/ip). Inside we define the variables for the host which can be refered in the play {{ host_var }}.

Handler
Can be used to handle the events as a seperate task.
notify: handlername will notify a task with matching name inside handler folder.
