#Build stage
FROM golang:1.19 AS build-env
WORKDIR /cosign
COPY . .
RUN make cosign

#Install Cosign 
FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
COPY --from=build-env /cosign/cosign /usr/local/bin/cosign
RUN chown root:0 /usr/local/bin/cosign && chmod g+wx /usr/local/bin/cosign

#Configure home directory
ENV HOME=/home
RUN chgrp -R 0 /${HOME} && chmod -R g=u /${HOME}

WORKDIR ${HOME}

# Makes sure's the pod in openshift stays running
CMD ["tail", "-f", "/dev/null"]