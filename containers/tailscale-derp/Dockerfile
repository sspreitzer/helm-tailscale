# https://tailscale.com/kb/1118/custom-derp-servers/
# -> "Custom DERP servers is currently in alpha."
FROM golang:alpine
ARG VERSION=main

RUN apk add git && go install tailscale.com/cmd/derper@${VERSION}

ENTRYPOINT [ "/go/bin/derper" ]
