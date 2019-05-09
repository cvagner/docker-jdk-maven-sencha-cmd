FROM maven:3.6.1-jdk-7

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ruby \
    libfreetype6 \
    fontconfig \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Fix the EC parameters error: (ref https://github.com/travis-ci/travis-ci/issues/8503)
RUN sudo wget "https://bouncycastle.org/download/bcprov-ext-jdk15on-158.jar" -O "${JAVA_HOME}"/jre/lib/ext/bcprov-ext-jdk15on-158.jar && \
  sudo perl -pi.bak -e 's/^(security\.provider\.)([0-9]+)/$1.($2+1)/ge' /etc/java-7-openjdk/security/java.security && \
  echo "security.provider.1=org.bouncycastle.jce.provider.BouncyCastleProvider" | sudo tee -a /etc/java-7-openjdk/security/java.security

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

