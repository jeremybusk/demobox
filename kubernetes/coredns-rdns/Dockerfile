FROM alpine
ADD https://github.com/coredns/coredns/releases/download/v1.8.1/coredns_1.8.1_linux_amd64.tgz coredns_1.8.1_linux_amd64.tgz
RUN tar xf coredns_1.8.1_linux_amd64.tgz
ADD https://raw.githubusercontent.com/jeremybusk/share/master/Corefile conf/Corefile
CMD ./coredns -conf conf/Corefile
