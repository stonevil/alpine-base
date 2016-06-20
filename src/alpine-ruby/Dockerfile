FROM stonevil/alpine-base
MAINTAINER stonevil@gmail.com

ENV GEM_UPGRADE_CMD="gem update"
ENV GEM_INSTALL_CMD="gem install --no-document --clear-sources"
ENV GEM_REMOVE_CMD="gem uninstall"

ENV RUBY_VERSION=${RUBY_VERSION:-2.3.1-r0}

LABEL com.stonevil.ruby.version=${RUBY_VERSION}

RUN ${APK_UPGRADE_CMD} && \
  ${APK_INSTALL_CMD} ruby=${RUBY_VERSION} && \
  ${APK_CACHE_RM} && \
  echo 'gem: --no-document' >> /etc/gemrc

CMD ruby --version
