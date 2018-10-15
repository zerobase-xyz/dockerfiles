FROM ubuntu:18.04

RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y wget curl vim tmux zsh git

RUN wget https://dl.google.com/go/go1.10.linux-amd64.tar.gz && tar -xvf go1.10.linux-amd64.tar.gz && mv go /usr/local

ENV GOROOT /usr/local/go
ENV GOPATH $HOME/go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

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

RUN git config --global ghq.root $GOPATH/src
