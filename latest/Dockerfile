FROM ghcr.io/cloudpunks/alpine:3.19@sha256:1137281fed3287438ce085bb5abde5b05f20b303d6b16e5ae62ea3bbe5737ff2
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
