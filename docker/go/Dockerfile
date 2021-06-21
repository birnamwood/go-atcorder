FROM golang:1.14

# コンテナ側作業ディレクトリ
WORKDIR /go/src/github.com/birnamwood/go-atcorder

# プロジェクトのソースをコンテナに追加
COPY ./ /go/src/github.com/birnamwood/go-atcorder

# 日本語セット
RUN apt-get update \
    && apt-get install -y locales \
    && locale-gen ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8
RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8
RUN ln -sf  /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# Package追加
RUN go get golang.org/x/tools/cmd/goimports
RUN go get golang.org/x/lint/golint
RUN go get github.com/securego/gosec
RUN go get -u github.com/kisielk/errcheck
RUN go get -u github.com/sonatard/noctx/cmd/noctx
## Lint TOOL
RUN go get github.com/golangci/golangci-lint/cmd/golangci-lint@v1.32.2