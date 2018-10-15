FROM golang:1.10.4-alpine

ENV GOPATH /root/go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

RUN apk update && apk add git vim tmux curl zsh

RUN cd $GOPATH && go get golang.org/x/tools/cmd/... \
#           github.com/golang/go \
           github.com/golang/lint/golint \
           github.com/nsf/gocode \
           github.com/rogpeppe/godef \
           github.com/jstemmer/gotags \
           github.com/motemen/ghq \
           github.com/motemen/gore \
           github.com/k0kubun/pp

RUN wget https://github.com/peco/peco/releases/download/v0.5.3/peco_linux_386.tar.gz && tar xzf peco_linux_386.tar.gz && chmod +x peco_linux_386/peco && mv peco_linux_386/peco /usr/local/bin/ && rm -rf peco*

RUN git clone https://github.com/zerobase-xyz/dotfiles.git /root/dotfiles && sh $HOME/dotfiles/setup.sh
