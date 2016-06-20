FROM quay.io/stonevil/alpine-glibc
MAINTAINER stonevil@gmail.com

ENV NPM_UPGRADE_CMD="npm update -g"
ENV NPM_INSTALL_CMD="npm install"
ENV NPM_REMOVE_CMD="npm uninstall"

ENV NODEJS_VERSION=${NODEJS_VERSION:-6.2.1-r0}

LABEL com.stonevil.nodejs.version=${NODEJS_VERSION}

RUN ${APK_UPGRADE_CMD} && \
  ${APK_INSTALL_CMD} nodejs=${NODEJS_VERSION} && \
  ${APK_CACHE_RM}

CMD node --version
