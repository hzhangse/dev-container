ARG GO_VERSION=1.21.8

FROM golang:${GO_VERSION}

ARG ROOTHOME=/Users/root

RUN mkdir -p $ROOTHOME
ENV HOME=$ROOTHOME

RUN apt-get update \
    && apt install --force-yes -y ca-certificates curl \
           build-essential gcc g++ \
           tzdata zip unzip vim wget \
           git openssh-client zsh bash net-tools tmux sudo wget \
    #
    # Clean up
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Modify Timezone
ENV TZ Asia/Shanghai
RUN cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Mark zsh as default shell
#RUN chsh -s /usr/bin/zsh



RUN go install github.com/go-delve/delve/cmd/dlv@v1.21.2



ENTRYPOINT [ "/bin/bash" ]
CMD ["-l"]
