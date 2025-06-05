# [choosenimでnim環境構築](https://qiita.com/honeytrap15/items/2c7ebe20cb69df8c53c9)
# [choosenim](https://github.com/dom96/choosenim)
# [INim](https://github.com/inim-repl/INim)
# [nimlsp](https://github.com/PMunch/nimlsp)
# [Jupyter notebookでNimを使い，グラフの可視化まで](https://qiita.com/SatoshiTerasaki/items/281c578c47f8ee497f3c)
FROM u1and0/python:latest
# Install Nim venv
RUN curl https://nim-lang.org/choosenim/init.sh -sSf -o /tmp/init.sh &&\
    chmod +x /tmp/init.sh &&\
    /tmp/init.sh -y &&\
    rm /tmp/init.sh
ENV PATH="/home/u1and0/.nimble/bin:${PATH}"
RUN choosenim -y stable
# pacman -S nim でも一式入ってくる(nimgrep nimsuggest 等)
# nimble install nimlsp は用意されているが、pacmanでnimをインストールしたから？
# nimlspのインストールに失敗する
# choosenimのほうがいいのか

# Instal Nim language sever & Repl
# Zeromq いる？？ jupyternimと一緒に同梱されているみたい
# Installing zmq@>= 1.2.1 & < 1.3.0
# Downloading https://github.com/nim-lang/nim-zmq using git
# Verifying dependencies for zmq@1.2.1
# Installing zmq@1.2.1
# Success: zmq installed successfully.

# goはここだけでしか使わないからbuild済みのefm-langserverをマルチビルドで持ってくるか
USER root
RUN pacman -Syu --noconfirm go zeromq

USER u1and0
RUN go install github.com/mattn/efm-langserver@latest
RUN nimble refresh &&\
    nimble -y install nimlsp inim jupyternim

LABEL maintainer="u1and0"\
      description="nim lang env with neovim and jupyter notebook"\
      version="rust:v1.0.2"
