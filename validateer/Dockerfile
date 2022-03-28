FROM integritee/integritee-demo-validateer:0.0.1

# Install 'dockerize'

ENV DEBIAN_FRONTEND=noninteractive
RUN curl --version
# Curl already installed in base image
# RUN apt update && apt install -y curl && rm -rf /var/lib/apt/lists/*

#RUN curl -sfL $(curl -s https://api.github.com/repos/powerman/dockerize/releases/latest | \
#    grep -i /dockerize-$(uname -s)-$(uname -m)\" | cut -d\" -f4) | \
#    install /dev/stdin /usr/local/bin/dockerize

RUN curl -sfL https://github.com/powerman/dockerize/releases/download/v0.11.5/dockerize-`uname -s`-`uname -m` | install /dev/stdin /usr/local/bin/dockerize

# Verify signature of 'dockerize'

RUN curl -sfL https://powerman.name/about/Powerman.asc | gpg --import
RUN curl -sfL https://github.com/powerman/dockerize/releases/download/v0.11.5/dockerize-`uname -s`-`uname -m`.asc >dockerize.asc
RUN gpg --verify dockerize.asc /usr/local/bin/dockerize

#RUN integritee --help

#CMD dockerize -wait tcp://web:9944 integritee -P 2090 -p 9944 run --skip-ra --dev