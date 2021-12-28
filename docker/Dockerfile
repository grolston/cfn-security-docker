FROM python:3.9-alpine

LABEL maintainer="George Rolston <https://github.com/grolston>"

# Setup for CFN-NAG
RUN apk add --update --no-cache npm ruby git ruby-rdoc
RUN apk add --no-cache ruby-webrick
RUN gem install cfn-nag

# Setup for CHECKOV.IO
ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3
RUN python -m ensurepip
RUN apk add --no-cache --virtual .build_deps build-base libffi-dev \
 && pip install --no-cache-dir -U checkov \
 && apk del .build_deps

# cfn-lint
RUN pip3 install cfn-lint

# Setup for CFN-GUARD
RUN apk add --no-cache cargo tree
RUN cargo install cfn-guard
ENV PATH "/root/.cargo/bin:${PATH}"