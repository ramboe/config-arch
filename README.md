# config-arch

https://chatgpt.com/c/d4952b73-422d-4702-8c4f-5b92714be486

## Steps for locally testing and debugging ansible with docker

### 1 - create docker file

go to /ansible/Dockerfile

```shell
# Use the latest Arch Linux image as the base
FROM archlinux:latest

# Run the necessary commands to install Ansible and create ansible.cfg
RUN pacman -Sy --noconfirm ansible-core ansible && \
    ansible-config init --disabled > ansible.cfg

# Set a default command, for example, to start a shell
CMD ["/bin/bash"]
```  

### 2 - build docker file

```shell
docker build -t custom-arch-ansible .
```  

### 3 - run the docker file  

```shell
docker run --detach --privileged --name archlinux_ansible_1 -it --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro --volume=$(pwd):/etc/ansible/roles/role_under_test:rw --volume=/home/ramboe/Documents/ansible:/root --volume=/mnt/data/source/config-arch/ansible:/root/clemens custom-arch-ansible:latest sh
docker run --detach --privileged --name archlinux_ansible_1 -it --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro --volume=$(pwd):/etc/ansible/roles/role_under_test:rw --volume=/mnt/data/source/config-arch/ansible:/root/ custom-arch-ansible:latest sh
```

### 4 - exec ansible playbook  

```shell
#docker exec --tty archlinux_ansible_1 env TERM=xterm ansible-playbook -vv /root/ansible/yaml/fem.yml
docker exec --tty archlinux_ansible_1 env TERM=xterm ansible-playbook -vv /root/clemens/fem.yml
docker exec --tty archlinux_ansible_1 env TERM=xterm ansible-playbook -vv /root/fem.yml
```  

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Framboe%2FQAyG_Qb4lz.png?alt=media&token=421054cf-e855-4c10-970f-a779239d6eb3)  
