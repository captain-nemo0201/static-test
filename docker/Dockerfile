# docker/Dockerfile
FROM ubuntu:24.04

# Установка пакетов
RUN apt-get update && \
    apt-get install -y openssh-server sudo && \
    apt-get clean && \
    mkdir -p /var/run/sshd

# Создание пользователя для SSH с заданием пароля
RUN useradd -m -s /bin/bash ansible && \
    echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Создвние директории .ssh
RUN mkdir -p /home/ansible/.ssh && \
    touch /home/ansible/.ssh/authorized_keys && \
    chown -R ansible:ansible /home/ansible/.ssh && \
    chmod 700 /home/ansible/.ssh && \
    chmod 600 /home/ansible/.ssh/authorized_keys

# Порты для SSH и Nginx
EXPOSE 22 80

ENTRYPOINT ["sshd", "-D"]

