FROM ubuntu:rolling
LABEL maintainer="info@valentineus.link"

ENV METEOR_ALLOW_SUPERUSER="true"

ARG RELEASE

RUN set -ex \
    && apt-get update \
    && apt-get --no-install-recommends --no-install-suggests --yes install \
        ca-certificates curl git openssl \
    && curl https://install.meteor.com | sed "s/^RELEASE=.*/RELEASE=${RELEASE}/g" | sh \
    && apt-get --purge --yes remove curl \
    && apt-get --purge --yes autoremove \
    && apt-get clean \
    && find /tmp -type f -exec rm {} \; \
    && find /var/cache -type f -exec rm {} \; \
    && find /var/lib/apt/lists -type f -exec rm {} \; \
    && find /var/log -type f -exec rm {} \; \
    && find /var/tmp -type f -exec rm {} \;

EXPOSE 3000

WORKDIR "/workspace"

CMD [ "/usr/local/bin/meteor", "run" ]