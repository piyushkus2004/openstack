# openstack
![images](https://github.com/piyushkus2004/openstack/assets/143024159/5cd157a9-7cfa-49ef-90fb-b67563c6a2a4)

## WHAT IS OPENSTACK ?
OpenStack is a free, open standard cloud computing platform. It is mostly deployed as infrastructure-as-a-service in public and private clouds where virtual servers and other resources are available to users.
### DEPLOY OPENSTACK THROUGH DEVSTACK

### Step 1: Update and Upgrade the System

```bash
apt update -y && apt upgrade -y
```
### Next reboot the system using the command

```bash
sudo reboot
```

### Step 2: Create Stack user and assign sudo priviledge
```bash
sudo adduser -s /bin/bash -d /opt/stack -m stack
sudo chmod +x /opt/stack
```
### Next, run the command below to assign sudo privileges to the user
```bash
echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
```
### Step 3: Install git and download DevStack
```bash
su - stack
```
### if git is missing in your ubuntu then use thins command
```bash
sudo apt install git -y
```
### Using git, clone devstack’s git repository as shown
```bash
git clone https://git.openstack.org/openstack-dev/devstack
```
### Step 4: Create devstack configuration file
```bash
cd devstack
```
### Then create a local.conf configuration file
```bash
vim local.conf
```
### Paste the following content
```bash
[[local|localrc]]
# Password for KeyStone, Database, RabbitMQ and Service
ADMIN_PASSWORD=StrongAdminSecret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
# Host IP - get your Server/VM IP address from ip addr command
HOST_IP=10.208.0.10
```
### Step 5: Install OpenStack with Devstack
```bash
./stack.sh
```
### Step 6: Accessing OpenStack on a web browser
```bash
https://server-ip/dashboard
```
