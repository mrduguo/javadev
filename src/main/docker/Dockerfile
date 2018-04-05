FROM mrduguo/java8

ENTRYPOINT ["bash"]

RUN apt-get update --fix-missing && \
    apt-get -y \
    install \
    telnet \
    net-tools \
    less \
    vim && \
    apt-get -y clean && \
    apt-get -q -y autoremove


RUN curl -O http://mirrors.ibiblio.org/apache/maven/maven-3/3.2.5/binaries/apache-maven-3.2.5-bin.tar.gz && \
    tar xzf apache-maven-3.2.5-bin.tar.gz -C /usr/local && \
    ln -s /usr/local/apache-maven-3.2.5/bin/mvn /usr/local/bin/mvn && \
    rm -f apache-maven-3.2.5-bin.tar.gz

RUN curl -O https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip && \
    unzip ngrok-stable-linux-amd64.zip && \
    mv ngrok /usr/local/bin/ngrok && \
    rm -f ngrok-stable-linux-amd64.zip && \
    curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && \
    chmod a+x /usr/local/bin/docker-compose

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash && \
    . ~/.nvm/nvm.sh && \
    nvm install node


RUN echo "===> Installing python, sudo, and supporting tools..."  && \
    apt-get update -y  &&  apt-get install --fix-missing          && \
    DEBIAN_FRONTEND=noninteractive         \
    apt-get install -y                     \
        python python-yaml sudo            \
        curl gcc python-pip python-dev libffi-dev libssl-dev  && \
    apt-get -y --purge remove python-cffi          && \
    pip install --upgrade cffi                     && \
    \
    \
    echo "===> Installing Ansible..."   && \
    pip install ansible                 && \
    \
    \
    echo "===> Installing handy tools (not absolutely required)..."  && \
    apt-get install -y sshpass openssh-client  && \
    \
    \
    echo "===> Removing unused APT resources..."                  && \
    apt-get -f -y --auto-remove remove \
                 gcc python-pip python-dev libffi-dev libssl-dev  && \
    apt-get clean                                                 && \
    rm -rf /var/lib/apt/lists/*  /tmp/*

#    docker build -t mrduguo/public:javadev-latest .
