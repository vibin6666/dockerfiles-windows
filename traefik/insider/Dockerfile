FROM microsoft/windowsservercore-insider as core
FROM microsoft/nanoserver-insider
COPY --from=core /windows/system32/netapi32.dll /windows/system32/netapi32.dll

ENV TRAEFIK_VERSION 1.5.1

ADD https://github.com/containous/traefik/releases/download/v${TRAEFIK_VERSION}/traefik_windows-amd64.exe /traefik.exe

VOLUME C:/etc/traefik
VOLUME C:/etc/ssl

EXPOSE 80
ENTRYPOINT ["/traefik", "--configfile=C:/etc/traefik/traefik.toml"]

# Metadata
LABEL org.label-schema.vendor="Containous" \
      org.label-schema.url="https://traefik.io" \
      org.label-schema.name="Traefik" \
      org.label-schema.description="A modern reverse-proxy" \
      org.label-schema.version="v${TRAEFIK_VERSION}" \
      org.label-schema.docker.schema-version="1.0"
