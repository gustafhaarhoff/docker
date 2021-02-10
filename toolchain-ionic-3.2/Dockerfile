# docker recipe for the cotech/toolchain-smsa-legacy image

FROM cotech/ubuntu-18-04-ssh-dev

ARG DEBIAN_FRONTEND=noninteractive

# install node 8.x and Ionic 3.2.0

USER root

RUN apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - &&\
    apt-get -y install nodejs &&\
    npm install -g ionic@3.2.0 &&\
    npm install -g cordova@8.0.0

# install java sdk
RUN apt-get -y install openjdk-8-jdk &&\
    echo "export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64" >> /home/dev/.bashrc

# install android sdk commandline tools
RUN apt-get -y install unzip &&\
    mkdir -p /usr/lib/android-sdk/cmdline-tools/latest &&\
    wget https://dl.google.com/android/repository/commandlinetools-linux-6858069_latest.zip &&\
    unzip commandlinetools-linux-6858069_latest.zip -d /usr/lib/android-sdk/cmdline-tools/latest &&\
    mv /usr/lib/android-sdk/cmdline-tools/latest/cmdline-tools/* /usr/lib/android-sdk/cmdline-tools/latest &&\
    rm commandlinetools-linux-6858069_latest.zip

# install Gradle
RUN apt-get -y install gradle

# setup ANDROID_HOME and PATH, and change ownership of the complete android-adk to the dev user
RUN echo "export ANDROID_HOME=/usr/lib/android-sdk" >> /home/dev/.bashrc &&\
    echo "export PATH=$PATH:/usr/lib/android-sdk/tools/bin" >> /home/dev/.bashrc &&\
    echo "export PATH=$PATH:/usr/lib/android-sdk/platform-tools" >> /home/dev/.bashrc &&\
    echo "export PATH=$PATH:/usr/lib/android-sdk/cmdline-tools/latest/bin" >> /home/dev/.bashrc &&\
    chown -R dev /usr/lib/android-sdk

USER dev

CMD echo "123" | sudo -S service ssh start && /bin/bash