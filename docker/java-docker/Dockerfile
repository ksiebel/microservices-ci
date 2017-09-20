FROM docker:latest

ENV JAVA_VERSION=8 \
    JAVA_UPDATE=60 \
    JAVA_BUILD=27 \
    JAVA_HOME=/usr/lib/jvm/default-jvm

# Here we use several hacks collected from https://github.com/gliderlabs/docker-alpine/issues/11:
# 1. install GLibc (which is not the cleanest solution at all)
# 2. hotfix /etc/nsswitch.conf, which is apperently required by glibc and is not used in Alpine Linux
ENV JAVA_DOWNLOAD=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz

RUN apk add --update wget ca-certificates && \
    cd /tmp && \
    wget "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.21-r2/glibc-2.21-r2.apk" \
         "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.21-r2/glibc-bin-2.21-r2.apk" && \
    apk add --allow-untrusted curl libstdc++ glibc-2.21-r2.apk glibc-bin-2.21-r2.apk && \
    /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib && \
    echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf && \
    mkdir -p /opt && curl -jfksSLH "Cookie: oraclelicense=accept-securebackup-cookie" \
      "${JAVA_DOWNLOAD:-$(curl -s https://lv.binarybabel.org/catalog-api/java/jdk8.txt?p=downloads.tgz)}" \
      | tar -xzf - -C /opt \
    && ln -s /opt/jdk1.*.0_* /opt/jdk \
    && rm -rf /opt/jdk/*src.zip \
              /opt/jdk/lib/missioncontrol \
              /opt/jdk/lib/visualvm \
              /opt/jdk/lib/*javafx* \
              /opt/jdk/jre/lib/plugin.jar \
              /opt/jdk/jre/lib/ext/jfxrt.jar \
              /opt/jdk/jre/bin/javaws \
              /opt/jdk/jre/lib/javaws.jar \
              /opt/jdk/jre/lib/desktop \
              /opt/jdk/jre/plugin \
              /opt/jdk/jre/lib/deploy* \
              /opt/jdk/jre/lib/*javafx* \
              /opt/jdk/jre/lib/*jfx* \
              /opt/jdk/jre/lib/amd64/libdecora_sse.so \
              /opt/jdk/jre/lib/amd64/libprism_*.so \
              /opt/jdk/jre/lib/amd64/libfxplugins.so \
              /opt/jdk/jre/lib/amd64/libglass.so \
              /opt/jdk/jre/lib/amd64/libgstreamer-lite.so \
              /opt/jdk/jre/lib/amd64/libjavafx*.so \
              /opt/jdk/jre/lib/amd64/libjfx*.so


  ENV JAVA_HOME /opt/jdk
  ENV PATH ${PATH}:${JAVA_HOME}/bin

  CMD ["java", "-version"]
