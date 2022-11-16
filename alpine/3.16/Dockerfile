FROM alpine:3.16.3@sha256:3d426b0bfc361d6e8303f51459f17782b219dece42a1c7fe463b6014b189c86d

LABEL maintainer1=deepak@breezeware.net

RUN apk add --no-cache curl bash \
    && rm -rf /var/cache/apk/*

RUN addgroup -g 2000 alpine \
    && adduser -u 2000 alpine -s /bin/bash -h /home/alpine -D -G alpine

RUN addgroup -g 1000 app \
    && adduser -u 1000 app -s /bin/bash -h /home/app -D -G app

ENTRYPOINT ["bash"]

# docker build & run commands
    # docker build -t breezewaredev/alpine:3.16.3 alpine/3.16/.
# Run alpine container
    # as root(default) user - docker run --rm -it breezewaredev/alpine:3.16.3
    # as app user - docker run --rm -it -u app breezewaredev/alpine:3.16.3
    # as alpine user - docker run --rm -it -u alpine breezewaredev/alpine:3.16.3
