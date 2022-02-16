# sudo docker build -t encrypted-operations .
# sudo docker run -d -p 1337:1337 --rm encrypted-operations

FROM ubuntu:20.04

RUN apt-get -y update && \
    apt-get -y upgrade 

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

USER build
EXPOSE 1337

CMD ./ynetd -p 1337 ./run.sh

#sudo mv Dockerfile build/ && sudo mv run.sh build/ && sudo mv flag.txt build/ && sudo mv ynetd build/
#sudo mv Dockerfile ../ && sudo mv run.sh ../ && sudo mv flag.txt ../ && sudo mv ynetd ../

