FROM ubuntu:22.04

# Instal·lació bàsica
RUN apt-get update && apt-get install -y \
    python3.10 python3.10-venv python3.10-distutils python3-pip \
    openssh-server supervisor gunicorn

# Crear usuaris i carpetes
RUN mkdir -p /var/run/sshd /var/log/supervisor /app /etc/supervisor/conf.d

# Afegir fitxers
COPY requirements.txt /app/
COPY app/ /app/
COPY supervisor/ /etc/supervisor/conf.d/

# Instal·lar dependències Python
RUN pip install -r /app/requirements.txt

# Configurar password root
RUN echo 'root:root' | chpasswd

# Crear un usuari no-root amb accés SSH
RUN useradd -m -s /bin/bash ubuntu && \
    echo "ubuntu:ubuntu" | chpasswd && \
    usermod -aG sudo ubuntu && \
    mkdir -p /home/ubuntu/.ssh && \
    chown -R ubuntu:ubuntu /home/ubuntu/.ssh && \
    chmod 700 /home/ubuntu/.ssh

EXPOSE 8000 22 9001
CMD ["/usr/bin/supervisord", "-n"]
