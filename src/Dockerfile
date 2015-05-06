# Используем Ubuntu в качестве базы
FROM ubuntu:latest

# Устанавливаем Firefox и PulseAudio
RUN apt-get update &&\
    apt-get install -yq &&\
    openssh-server libpulse0 pulseaudio xauth firefox

# Добавляем наш публичный ключ в SSH
ADD id_rsa.pub /root/id_rsa.pub
RUN mkdir /root/.ssh &&\
    cat /root/id_rsa.pub > /root/.ssh/authorized_keys

# Включаем форвардинг X11 и root-доступ в SSH
RUN echo 'X11Forwarding yes\nPermitRootLogin yes' >> /etc/ssh/sshd_config

# Без этого каталога SSH работать не будет 
RUN mkdir /var/run/sshd

