# Python dev docker image
#
# Usage:
#   In host machine's shell
#     $ docker pull u1and0/python
#     $ docker run -it --rm -v `pwd`:/work -w /work u1and0/python
#
#   Using other command with activating `conda`
#     $ docker run -it --rm -v `pwd`:/work -w /work\
#           u1and0/python bash -c ". .bashrc && python"
#     $ docker run -it --rm -v `pwd`:/work -w /work\
#           u1and0/python bash -c ". .bashrc && ipython"
#     $ docker run -it --rm -v `pwd`:/work -w /work\
#           u1and0/python bash -c ". .bashrc && nvim"
#     $ docker run -P -it --rm -v `pwd`:/work -w /work\
#           u1and0/python bash -c ". .bashrc && jupyter notebook"
#
#     $ docker run -it --rm -v `pwd`:/work -w /work -p 8888:8888 \
#            u1and0/python bash -c 'source /etc/profile.d/conda.sh && conda activate && ipython'  
#
#   In contaner
#     Just type
#     $ ipython
#         or
#     $ jupyter lab
#         or
#     $ nvim

FROM u1and0/zplug:latest

USER root

RUN pacman -Syyu --noconfirm python-pip python-pipenv otf-ipafont &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns



# Base packages
USER u1and0
COPY ./requirements.txt /home/u1and0/build/
RUN pipenv install -r /home/u1and0/build/requirements.txt

# Docker build failed
#
# (Deprecated) Installing extensions with the jupyter labextension install command is now deprecated and will be removed in a future major version of JupyterLab.
# Users should manage prebuilt extensions with package managers like pip and conda, and extension authors are encouraged to distribute their extensions as prebuilt packages
#
# RUN source /etc/profile.d/conda.sh &&\
#     conda activate &&\
#     jupyter labextension install @lckr/jupyterlab_variableinspector@3.0.7

CMD ["pipenv", "shell"]
EXPOSE 8888

# Usage:
#
# bash に入る
# $ docker run -it --rm u1and0/python
# (base) u1and0@4270a289dfbf:~$

# jupyter labを立ち上げる
# $ docker run -it --rm u1and0/python jupyter lab


LABEL maintainer="u1and0 <e01.ando60@gmail.com>"\
      description="python dev container"\
      description.ja="python開発用コンテナ。ipython, jupyter notebook, neovimによる開発"\
      build_version="python:v2.0.0"
