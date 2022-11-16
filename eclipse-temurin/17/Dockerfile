FROM breezewaredev/alpine:3.16.3@sha256:7f05bc544a219237b485fba8c7818fa431b58565ea7cb1a92118b6ee61639d92

LABEL maintainer1=deepak@breezeware.net

RUN addgroup -g 2001 java \
    && adduser -u 2001 java -s /bin/bash -h /home/java -D -G java

ARG JAVA_JRE_VERSION=17.0.1+8
ARG JAVA_JRE_17_DOWNLOAD_SHA256="043b3169b3d1f6fbf0d807e61b9f94d167d08e13dd2f4fb76786e60ee65e5ae5"
ARG JAVA_JRE_17_DOWNLOAD_URL='https://github.com/adoptium/temurin17-binaries/releases/download/jdk-17.0.2%2B8/OpenJDK17U-jre_x64_alpine-linux_hotspot_17.0.2_8.tar.gz'

RUN wget -O /tmp/openjdk-17-jre.tar.gz ${JAVA_JRE_17_DOWNLOAD_URL} \
    && ls -alth /tmp/openjdk-17-jre.tar.gz \
    && echo "${JAVA_JRE_17_DOWNLOAD_SHA256} */tmp/openjdk-17-jre.tar.gz" | sha256sum -c - \
    && mkdir -p /usr/local/java \
    && tar --extract \
	      --file /tmp/openjdk-17-jre.tar.gz \
	      --directory /usr/local/java \
	      --strip-components 1 \
	      --no-same-owner \
    && rm -rf /tmp/openjdk-17-jre.tar.gz

ENV JAVA_HOME=/usr/local/java \
    PATH="/usr/local/java/bin:$PATH"

RUN echo Verifying installation ... \
    && java --version \
    && echo Complete.

# docker build & run commands
    # docker build -t breezewaredev/eclipse-temurin:17.0.2_8-jre-alpine eclipse-temurin/17/.
# Run eclipse-temurin container
    # as root(default) user - docker run --rm -it breezewaredev/eclipse-temurin:17.0.2_8-jre-alpine
    # as app user - docker run --rm -it -u app breezewaredev/eclipse-temurin:17.0.2_8-jre-alpine
    # as alpine user - docker run --rm -it -u alpine breezewaredev/eclipse-temurin:17.0.2_8-jre-alpine
    # as java user - docker run --rm -it -u java breezewaredev/eclipse-temurin:17.0.2_8-jre-alpine
