FROM ubuntu:rolling
LABEL maintainer="info@valentineus.link"

ENV METEOR_ALLOW_SUPERUSER="true"
WORKDIR "/workspace"

RUN set -ex \
    && apt-get update \
    && apt-get --no-install-recommends --no-install-suggests --yes install \
        build-essential \
        ca-certificates \
        curl \
        git \
        openssl \
    && curl https://install.meteor.com | sh \
    && apt-get --purge --yes autoremove \
    && apt-get clean \
    && find /tmp -type f -exec rm {} \; \
    && find /var/cache -type f -exec rm {} \; \
    && find /var/lib/apt/lists -type f -exec rm {} \; \
    && find /var/log -type f -exec rm {} \; \
    && find /var/tmp -type f -exec rm {} \;

EXPOSE 3000
CMD [ "/usr/local/bin/meteor", "run" ]