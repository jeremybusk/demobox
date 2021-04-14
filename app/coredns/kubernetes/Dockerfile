# FROM debian:buster-slim
FROM alpine
WORKDIR /app
ADD https://github.com/coredns/coredns/releases/download/v1.8.1/coredns_1.8.1_linux_amd64.tgz coredns_1.8.1_linux_amd64.tgz
RUN tar xf coredns_1.8.1_linux_amd64.tgz
ADD https://raw.githubusercontent.com/jeremybusk/share/master/Corefile conf/Corefile
# CMD ./coredns -conf conf/Corefile


# FROM coredns/coredns:latest

LABEL maintainer="Jeremy Busk"

EXPOSE 53 53/udp
# ADD . /app/
COPY conf/ /app/
# RUN ls -la /app/*
# COPY . /app
# VOLUME ["/etc/coredns"]
# ENTRYPOINT ["/coredns"]
# CMD ["-conf", "/etc/coredns/Corefile"]
 # CMD["-conf", "Corefile"]
CMD ./coredns -conf Corefile
