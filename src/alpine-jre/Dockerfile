FROM stonevil/alpine-glibc
MAINTAINER stonevil@gmail.com

ENV JAVA_HOME_BASE=${JAVA_HOME_BASE:-/opt}
ENV JAVA_HOME $JAVA_HOME_BASE/jre

ENV LANG C.UTF-8
ENV JAVA_VERSION=${JAVA_VERSION:-8}
ENV JAVA_UPDATE=${JAVA_UPDATE:-92}
ENV JAVA_BUILD=${JAVA_BUILD:-14}
ENV JAVA_PACKAGE=${JAVA_PACKAGE:-server-jre}
ENV JRE_URL=http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}u${JAVA_UPDATE}-b${JAVA_BUILD}/${JAVA_PACKAGE}-${JAVA_VERSION}u${JAVA_UPDATE}-linux-x64.tar.gz

ENV PATH $JAVA_HOME/bin:$PATH

LABEL com.stonevil.jre.version=${JAVA_VERSION}.${JAVA_UPDATE}.${JAVA_BUILD}

RUN mkdir ${JAVA_HOME_BASE} && cd ${JAVA_HOME_BASE} && (${SOFTWARE_DOWNLOAD_CMD} --junk-session-cookies --cookie "oraclelicense=accept-securebackup-cookie" ${JRE_URL} | gunzip -c - | tar xf - ) && \
  chown -Rf root:root ${JAVA_HOME_BASE}/jdk* && \
  ln -s ${JAVA_HOME_BASE}/jdk* ${JAVA_HOME} && \
  ln -s ${JAVA_HOME}/bin/java /usr/bin/java && \
  rm -rf ${JAVA_HOME}/*src.zip && \
  rm -rf ${JAVA_HOME}/lib/missioncontrol \
    ${JAVA_HOME}/lib/visualvm \
    ${JAVA_HOME}/lib/*javafx* \
    ${JAVA_HOME}/jre/lib/plugin.jar \
    ${JAVA_HOME}/jre/lib/ext/jfxrt.jar \
    ${JAVA_HOME}/jre/bin/javaws \
    ${JAVA_HOME}/jre/lib/javaws.jar \
    ${JAVA_HOME}/jre/lib/desktop \
    ${JAVA_HOME}/jre/plugin \
    ${JAVA_HOME}/jre/lib/deploy* \
    ${JAVA_HOME}/jre/lib/*javafx* \
    ${JAVA_HOME}/jre/lib/*jfx* \
    ${JAVA_HOME}/jre/lib/amd64/libdecora_sse.so \
    ${JAVA_HOME}/jre/lib/amd64/libprism_*.so \
    ${JAVA_HOME}/jre/lib/amd64/libfxplugins.so \
    ${JAVA_HOME}/jre/lib/amd64/libglass.so \
    ${JAVA_HOME}/jre/lib/amd64/libgstreamer-lite.so \
    ${JAVA_HOME}/jre/lib/amd64/libjavafx*.so \
    ${JAVA_HOME}/jre/lib/amd64/libjfx*.so && \
  rm -rf ${JAVA_HOME}/jre/bin/jjs \
    ${JAVA_HOME}/jre/bin/keytool \
    ${JAVA_HOME}/jre/bin/orbd \
    ${JAVA_HOME}/jre/bin/pack200 \
    ${JAVA_HOME}/jre/bin/policytool \
    ${JAVA_HOME}/jre/bin/rmid \
    ${JAVA_HOME}/jre/bin/rmiregistry \
    ${JAVA_HOME}/jre/bin/servertool \
    ${JAVA_HOME}/jre/bin/tnameserv \
    ${JAVA_HOME}/jre/bin/unpack200 \
    ${JAVA_HOME}/jre/lib/ext/nashorn.jar \
    ${JAVA_HOME}/jre/lib/jfr.jar \
    ${JAVA_HOME}/jre/lib/jfr \
    ${JAVA_HOME}/jre/lib/oblique-fonts

CMD java -version
