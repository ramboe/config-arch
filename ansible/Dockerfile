FROM ubuntu:latest

# Update package list and install software-properties-common
RUN apt update && \
    apt install -y software-properties-common && \
    echo "Installed software-properties-common"

# Add Ansible PPA
RUN add-apt-repository --yes --update ppa:ansible/ansible && \
    echo "Added Ansible PPA"

# Update package list again
RUN apt update && \
    echo "Updated package list after adding Ansible PPA"

# Install Ansible and ansible-core
RUN apt install -y ansible && \
    echo "Installed Ansible" && \
    apt install -y ansible-core && \
    echo "Installed ansible-core"

# Create the ansible.cfg file
RUN ansible-config init --disabled > ansible.cfg && \
    echo "Created ansible.cfg"

# Set a default command to start a shell
CMD ["/bin/bash"]
