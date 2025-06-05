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

# 仮想環境の構築
ENV VENV_PATH="/opt/venv"
ENV PATH="${VENV_PATH}/bin:$PATH"
RUN uv venv $VENV_PATH

# 開発用パッケージのインストール
COPY ./requirements.txt /tmp/
RUN uv pip install --python ${VENV_PATH}/bin/python -r /tmp/requirements.txt &&\
    rm /tmp/requirements.txt

USER u1and0
EXPOSE 8888
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--allow-root"]

LABEL maintainer="u1and0"\
      description="python dev container"\
      description.ja="python開発用コンテナ。ipython, jupyter notebook, neovimによる開発"\
      build_version="python:v2.0.0"
