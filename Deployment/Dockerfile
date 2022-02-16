
FROM ubuntu:20.04

RUN apt-get -y update && \
    apt-get -y upgrade && \
    apt -yqq install python3-dev python3-pip 

RUN pip install pycryptodome 

RUN useradd -m ctf
RUN echo "ctf:ctf" | chpasswd  && adduser ctf sudo

##########################3

ADD ynetd /home/ctf
ADD run.sh /home/ctf

ADD mtproto.py /home/ctf
ADD secret.py /home/ctf

WORKDIR /home/ctf

RUN chown -R root:root /home/ctf

RUN chmod +x run.sh
RUN chmod +x ynetd
RUN chmod +x mtproto.py

USER ctf
EXPOSE 1337

CMD ./ynetd -p 1337 ./mtproto.py
