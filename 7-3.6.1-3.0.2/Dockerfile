FROM maven:3.6.1-jdk-7

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ruby \
    libfreetype6 \
    fontconfig \
    && rm -rf /var/lib/apt/lists/*

# Install Bouncycastle Security Provider (fix for invalid prime number connection error) [from jollydays/java-microservice-base]
ENV BC_VERSION=jdk15on-157
RUN curl -jksSL http://bouncycastle.org/download/bcprov-$BC_VERSION.jar > $JAVA_HOME/jre/lib/ext/bcprov-$BC_VERSION.jar &&\
    curl -jksSL http://bouncycastle.org/download/bcprov-ext-$BC_VERSION.jar > $JAVA_HOME/jre/lib/ext/bcprov-ext-$BC_VERSION.jar
COPY java.security $JAVA_HOME/jre/lib/security/

# Installing SenchaCmd
RUN curl --silent https://cdn.sencha.com/cmd/3.0.2.288/SenchaCmd-3.0.2.288-linux-x64.run.zip -o /tmp/sencha.zip && \
    unzip /tmp/sencha.zip -d /tmp  && \
    unlink /tmp/sencha.zip  && \
    chmod o+x /tmp/SenchaCmd-3.0.2.288-linux-x64.run  && \
    echo -e '\n\n\n\n\n\ny\n/opt\n\n' | /tmp/SenchaCmd-3.0.2.288-linux-x64.run  && \
    unlink /tmp/SenchaCmd-3.0.2.288-linux-x64.run

# Cleaning
RUN apt-get clean

WORKDIR /app

ENV PATH="/opt/Sencha/Cmd/3.0.2.288:${PATH}"

