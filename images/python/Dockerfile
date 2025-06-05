# Python dev docker image
#
# Usage:
#   In host machine's shell
#     $ docker pull u1and0/python
#     $ docker run -it --rm -v `pwd`:/work -w /work u1and0/python
#
#   Using other command with activating `pipenv`
#
#       Open terminal
#     $ docker run -it --rm -v `pwd`:/work -w /work u1and0/python\
#           pipenv shell
#
#       Run jupyter console
#     $ docker run -it --rm -v `pwd`:/work -w /work u1and0/python\
#           pipenv run jupyter console
#
#       Any port
#     $ docker run -it --rm -v `pwd`:/work -w /work -P u1and0/python\
#           pipenv run jupyter lab
#
#       Specify port 8888
#     $ docker run -it --rm -v `pwd`:/work -w /work -p 8888:8888 u1and0/python\
#           pipenv run jupyter lab

FROM u1and0/zplug:latest

# パッケージマネージャーの準備
USER root
RUN pacman -Syyu --noconfirm uv otf-ipafont &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns

ARG USERNAME=u1and0
# 仮想環境の場所
ENV APP_HOME="/home/${USERNAME}"
ENV VENV_PATH="${APP_HOME}/.venv"

# 作業ディレクトリとユーザー切り替え
USER $USERNAME
WORKDIR $APP_HOME
ENV PATH="${VENV_PATH}/bin:${APP_HOME}/.local/bin:$PATH"

# 仮想環境の構築
RUN uv venv $VENV_PATH --python $(which python)

# 開発用パッケージのインストール
COPY --chown=$USERNAME:$USERNAME ./requirements.txt /tmp/
RUN uv pip install -r /tmp/requirements.txt &&\
    rm /tmp/requirements.txt
EXPOSE 8888
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--allow-root"]

LABEL maintainer="u1and0"\
      description="python dev container"\
      description.ja="python開発用コンテナ。ipython, jupyter notebook, neovimによる開発"\
      build_version="python:v2.0.0"
