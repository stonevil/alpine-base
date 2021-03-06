FROM quay.io/stonevil/alpine-base
MAINTAINER stonevil@gmail.com

ENV ALPINE_GLIBC_BASE_URL=${ALPINE_GLIBC_BASE_URL:-https://github.com/andyshinn/alpine-pkg-glibc/releases/download}
ENV ALPINE_GLIBC_PACKAGE_VERSION=${ALPINE_GLIBC_PACKAGE_VERSION:-2.23-r1}
ENV ALPINE_GLIBC_BASE_PACKAGE_FILENAME=${ALPINE_GLIBC_BIN_PACKAGE_FILENAME:-glibc-$ALPINE_GLIBC_PACKAGE_VERSION.apk}
ENV ALPINE_GLIBC_BIN_PACKAGE_FILENAME=${ALPINE_GLIBC_BIN_PACKAGE_FILENAME:-glibc-bin-$ALPINE_GLIBC_PACKAGE_VERSION.apk}
ENV ALPINE_GLIBC_I18N_PACKAGE_FILENAME=${ALPINE_GLIBC_I18N_PACKAGE_FILENAME:-glibc-i18n-$ALPINE_GLIBC_PACKAGE_VERSION.apk}

LABEL com.stonevil.glibc.version=${ALPINE_GLIBC_PACKAGE_VERSION}

RUN ${APK_UPGRADE_CMD} && \
  ${SOFTWARE_DOWNLOAD_CMD} -o "/tmp/${ALPINE_GLIBC_BASE_PACKAGE_FILENAME}" "${ALPINE_GLIBC_BASE_URL}/${ALPINE_GLIBC_PACKAGE_VERSION}/${ALPINE_GLIBC_BASE_PACKAGE_FILENAME}" && \
  ${SOFTWARE_DOWNLOAD_CMD} -o "/tmp/${ALPINE_GLIBC_BIN_PACKAGE_FILENAME}" "${ALPINE_GLIBC_BASE_URL}/${ALPINE_GLIBC_PACKAGE_VERSION}/${ALPINE_GLIBC_BIN_PACKAGE_FILENAME}" && \
  ${SOFTWARE_DOWNLOAD_CMD} -o "/tmp/${ALPINE_GLIBC_I18N_PACKAGE_FILENAME}" "${ALPINE_GLIBC_BASE_URL}/${ALPINE_GLIBC_PACKAGE_VERSION}/${ALPINE_GLIBC_I18N_PACKAGE_FILENAME}" && \
  ${APK_INSTALL_CMD} --allow-untrusted "/tmp/${ALPINE_GLIBC_BASE_PACKAGE_FILENAME}" "/tmp/${ALPINE_GLIBC_BIN_PACKAGE_FILENAME}" "/tmp/${ALPINE_GLIBC_I18N_PACKAGE_FILENAME}" && \
  /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 C.UTF-8 || true && \
  echo "export LANG=C.UTF-8" > /etc/profile.d/locale.sh && \
  apk del glibc-i18n && \
  ${APK_CACHE_RM}

CMD /bin/bash --version ; \
  ldd --version ; \
  /usr/glibc-compat/bin/pldd --version
