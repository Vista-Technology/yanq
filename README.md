# YANQ
YANQ: Yet Another NetOps Quickstart - Talk IDI (Incontro DevOps Italia) 2021

## How to reproduce the demo environment

to reproduce this demo enviroment there are some requirements:
- Docker
- Docker Compose
- Ansible

### AWX

First of all, we need to clone AWX 17.1.0 and move to `installer\`

```bash
git clone -b 17.1.0 https://github.com/ansible/awx.git
cd installer\
```

in this directory you will find:
```
installer
|-- build.yml
|-- install.yml
|-- inventory
`-- roles
```
Inside of `inventory`, you will find all parameters that you might need to change like `admin_user` and `admin_password`. 
You might want to change the default `admin:password` with something more robust like `andrea:IDI2021` 🙂 .

then, run the playbook `install.yml` with the inventory previously edited.
```bash
sudo ansible-playbook install.yml -i inventory
```
> This procedure will take some time and may take more than one try to reach the end.

when everything is complete you will find a new directory `~\.awx` in this directory you will find the docker-compose used to run all the AWX stack.

At this point, everything is up and running!
![Screenshot 2021-10-13 at 17-22-58 Ansible AWX](https://user-images.githubusercontent.com/34337409/137163989-66a8681c-a737-43cb-b934-b432102d66a2.png)

> You can access AWX by the IP address of your host. By default, the Web service will be exposed at port 80.

### everything else

All the other components of the stack like Grafana, Prometheus, Gitea, Batfish, Nautobot, and the exporters will be deployed in a single docker-compose.yml


