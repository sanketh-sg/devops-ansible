Created a node application and deployed it using ansible.

The app was accessible inside the docker VM but not in EC2 since I did not expose the port 80. after exposing the challeng was to port fwd it a port in EC2. since the container is already running one way to do it is to, use "socat"

sudo nohup socat TCP-LISTEN:8080,fork TCP:192.168.60.4 &
nohup make it run in background later kill it 
ps aux | grep nohup

Forever tracks the Node apps it manages, and we use Forever’s list option to print
a list of running apps. The first time we run this playbook, the list will obviously
be empty—but on future runs, if the app is running, we don’t want to start another
instance of it. 