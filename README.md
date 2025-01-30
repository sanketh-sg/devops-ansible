AWS keeps changing EC2 instance IP whenever restarted do I need to add it known_hosts each time

Ansible by defalut avoids using files in world writable folder(rwx) and uses the default config in /etc/ansible/ansible.cfg

Files mounted from host to wsl will have full permissions hence keeping files inside wsl. Now asnible can recognise file local folder.
local >> env variable >> global