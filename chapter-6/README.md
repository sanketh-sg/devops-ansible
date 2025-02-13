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