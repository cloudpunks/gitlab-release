FROM ghcr.io/cloudpunks/alpine:3.19@sha256:69022bf9cf0b23fa705a2da7b8c9527cf4388eea5ec982d25f21e1d94e8bec66
ENTRYPOINT [""]

# renovate: datasource=gitlab-releases depName=gitlab-org/release-cli
ENV GITLAB_RELEASE_VERSION=0.16.0

ARG TARGETARCH

RUN apk update && \
  apk upgrade && \
  case "${TARGETARCH}" in \
    'amd64') \
      curl -sSLo /usr/bin/release-cli https://gitlab.com/gitlab-org/release-cli/-/releases/v${GITLAB_RELEASE_VERSION}/downloads/bin/release-cli-linux-amd64; \
      ;; \
    'arm64') \
      curl -sSLo /usr/bin/release-cli https://gitlab.com/gitlab-org/release-cli/-/releases/v${GITLAB_RELEASE_VERSION}/downloads/bin/release-cli-linux-arm64; \
      ;; \
    *) echo >&2 "error: unsupported architecture '${TARGETARCH}'"; exit 1 ;; \
  esac && \
  chmod +x /usr/bin/release-cli && \
  rm -rf /var/cache/apk/*
