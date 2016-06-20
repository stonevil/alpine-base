FROM alpine:edge
MAINTAINER stonevil@gmail.com

ENV SOFTWARE_DOWNLOAD_TIMEOUT=${SOFTWARE_DOWNLOAD_TIMEOUT:-300}
ENV SOFTWARE_DOWNLOAD_RETRIES=${SOFTWARE_DOWNLOAD_RETRIES:-5}
ENV SOFTWARE_DOWNLOAD_RETRIES_DELAY=${SOFTWARE_DOWNLOAD_RETRIES_DELAY:-10}
ENV SOFTWARE_DOWNLOAD_CMD="curl --connect-timeout ${SOFTWARE_DOWNLOAD_TIMEOUT} --retry ${SOFTWARE_DOWNLOAD_RETRIES} --retry-delay ${SOFTWARE_DOWNLOAD_RETRIES_DELAY} --location"

ENV APK_UPGRADE_CMD="apk update && apk upgrade"
ENV APK_INSTALL_CMD="apk --update add"
ENV APK_REMOVE_CMD="apk del"
ENV APK_CACHE_RM="rm -rf /var/cache/apk/* && rm -rf /tmp/*.apk && rm -rf /tmp/*.tar*"

ENV GOSU_VERSION=${GOSU_VERSION:-1.9}
ENV CONFD_VERSION=${CONFD_VERSION:-0.11.0}

LABEL architecture="amd64" \
  vendor=stonevil \
  com.stonevil.os="alpine" \
  com.stonevil.os.version="edge" \
  com.stonevil.gosu.version=${GOSU_VERSION} \
  com.stonevil.confd.version=${CONFD_VERSION}

RUN ${APK_UPGRADE_CMD} && \
  ${APK_INSTALL_CMD} bash ca-certificates curl && \
  ${APK_CACHE_RM} && \
  echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf && \
  ${SOFTWARE_DOWNLOAD_CMD} -o /usr/bin/gosu https://github.com/tianon/gosu/releases/download/${GOSU_VERSION}/gosu-amd64 && chmod +x /usr/bin/gosu && \
  ${SOFTWARE_DOWNLOAD_CMD} -o /usr/bin/confd https://github.com/kelseyhightower/confd/releases/download/v${CONFD_VERSION}/confd-${CONFD_VERSION}-linux-amd64 && chmod +x /usr/bin/confd

CMD /bin/bash --version ; \
  confd --version ; \
  gosu
