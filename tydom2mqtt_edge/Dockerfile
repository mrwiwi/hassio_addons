ARG BUILD_FROM=hassioaddons/base:latest
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

# Copy data for add-on
COPY . /

COPY requirements.txt /tmp/
RUN mkdir -p /opt
RUN apk add --no-cache python3

RUN pip3 install --requirement /tmp/requirements.txt

RUN curl -L -s \
        "https://github.com/mrwiwi/tydom2mqtt/archive/v1.2.4.tar.gz" \
        | tar zxvf - -C /opt/

RUN mv /opt/tydom2mqtt* /opt/tydom2mqtt
RUN chmod a+x /run.sh

# WORKDIR /data

CMD [ "/run.sh" ]
