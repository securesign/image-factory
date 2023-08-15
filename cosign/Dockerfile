FROM golang:1.19 AS build-env
WORKDIR /cosign
COPY . .
RUN make cosign

FROM cgr.dev/chainguard/static:latest
COPY ./cosign /usr/local/bin/cosign
ENTRYPOINT [ "cosign" ]