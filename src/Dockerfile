FROM golang:1.10-alpine3.7

ARG pkg=github.com/realroy/spa-lab-final

RUN apk add --no-cache ca-certificates

COPY . $GOPATH/src/$pkg

RUN set -ex \
      && apk add --no-cache --virtual .build-deps \
              git \
      && go get -v $pkg/... \
      && apk del .build-deps

RUN go install $pkg/...

WORKDIR $GOPATH/src/$pkg/app

CMD echo "Use the app or pubsub_worker commands."; exit 1