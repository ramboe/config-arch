# Use the latest Arch Linux image as the base
FROM ubuntu:latest

# Run the necessary commands to install Ansible and create ansible.cfg
RUN apt update --fix-missing && \
    apt-get install -y software-properties-common && \
    apt-add-repository ppa:ansible/ansible && \
    apt update && \
    apt install -y ansible && \
    apt install -y ansible-core && \
    ansible-config init --disabled > ansible.cfg

# Set a default command, for example, to start a shell
CMD ["/bin/bash"]