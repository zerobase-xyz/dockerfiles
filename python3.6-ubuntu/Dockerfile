FROM python:3.6

RUN apt-get update && apt-get upgrade -y && apt-get install -y git curl zsh build-essential automake libevent-dev ncurses-dev

RUN git clone https://github.com/vim/vim.git /tmp/vim && cd /tmp/vim && ./configure --enable-python3interp && make && make install && rm -rf /tmp/vim

WORKDIR /root

RUN git clone https://github.com/zerobase-xyz/dotfiles.git && sh $HOME/dotfiles/setup.sh

COPY requirements.txt ./

ENV PYTHONIOENCODING utf-8

RUN pip install --no-cache-dir -r requirements.txt
