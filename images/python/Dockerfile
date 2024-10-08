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

USER root
RUN pacman -Syyu --noconfirm python-pip python-pipenv otf-ipafont &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns

# Base packages
USER u1and0
COPY ./requirements.txt /home/u1and0/build/
RUN pipenv install -r /home/u1and0/build/requirements.txt
CMD ["pipenv", "shell"]
EXPOSE 8888

LABEL maintainer="u1and0 <e01.ando60@gmail.com>"\
      description="python dev container"\
      description.ja="python開発用コンテナ。ipython, jupyter notebook, neovimによる開発"\
      build_version="python:v2.0.0"
