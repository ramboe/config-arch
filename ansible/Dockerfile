# Use the latest Arch Linux image as the base
FROM archlinux:latest

# Run the necessary commands to install Ansible and create ansible.cfg
RUN pacman -Sy --noconfirm ansible-core ansible && \
    ansible-config init --disabled > ansible.cfg

# Set a default command, for example, to start a shell
CMD ["/bin/bash"]
