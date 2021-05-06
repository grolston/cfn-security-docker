FROM alpine:3.12.4

LABEL maintainer="George Rolston <https://github.com/grolston>"

# Setup for CFN-NAG
RUN apk add --update --no-cache npm ruby git ruby-rdoc
RUN apk add --no-cache ruby-webrick
RUN gem install cfn-nag

# Setup for CHECKOV.IO
ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN python3 -m ensurepip
RUN pip3 install --no-cache --upgrade pip setuptools
RUN pip3 install checkov

# cfn-lint
RUN pip3 install cfn-lint