FROM ghcr.io/kithlo-server/worker:latest

WORKDIR /workspace

COPY --chmod=0755 git-config.sh /usr/local/bin/git-config.sh
COPY --chmod=0755 shell-entrypoint.sh /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
