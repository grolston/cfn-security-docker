FROM alpine:3.12.1

# Setup for CFN-NAG
RUN apk add --update npm ruby git wget ruby-rdoc
RUN apk add ruby-webrick
RUN gem install cfn-nag
RUN npm install -g cfn-lint

# Setup for CHECKOV.IO
ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN python3 -m ensurepip
RUN pip3 install --no-cache --upgrade pip setuptools
RUN pip install checkov
