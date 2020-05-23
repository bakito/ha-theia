FROM theiaide/theia as theia

ARG BUILD_FROM=hassioaddons/debian-base:3.2.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

RUN \
    apk add --no-cache \
    git=2.24.3-r0 \
    nodejs=12.15.0-r1 \
    npm=12.15.0-r1

ENV HOME /home/theia
WORKDIR /home/theia
COPY --from=theia  /home/theia /home/theia
EXPOSE 3000
ENV SHELL=/bin/bash \
    THEIA_DEFAULT_PLUGINS=local-dir:/home/theia/plugins
ENV USE_LOCAL_GIT true
ENTRYPOINT [ "node", "/home/theia/src-gen/backend/main.js", "/home/project", "--hostname=0.0.0.0" ]

