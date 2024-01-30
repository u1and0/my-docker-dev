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

RUN pacman -Syyu --noconfirm python-pip otf-ipafont &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns


# Install miniconda3-latest & restore conda packages
# Install libtiff5 for %matplotlib inline on jupyter lab notebook
USER u1and0
RUN yay -Syyu --noconfirm miniconda3 libtiff5 &&\
    yay -Scc

# Base packages
USER root
ENV PATH=/etc/profile.d:$PATH
RUN ln -s /opt/miniconda3/etc/profile.d/conda.sh /etc/profile.d/conda.sh
RUN source conda.sh &&\
    conda activate &&\
    conda install --quiet --yes \
        --channel conda-forge \
        'python-lsp-server[all]' \
        autopep8 \
        beautifulsoup4 \
        black \
        conda-build \
        cufflinks-py \
        dash \
        dash-core-components \
        dash-html-components \
        dash-renderer \
        dash-table \
        fastapi \
        flake8 \
        h5py \
        ipython \
        ipywidgets \
        isort \
        jinja2 \
        jupyter \
        jupyter_contrib_nbextensions \
        jupyterlab \
        jupyterlab-language-pack-ja-jp \
        jupyterlab-lsp \
        jupyterlab-variableinspector \
        jupyterlab_code_formatter \
        jupyterlab_vim \
        jupyterthemes \
        line_profiler \
        matplotlib \
        more-itertools \
        mypy \
        neovim \
        nodejs \
        notebook \
        numpy \
        pandas \
        plotly \
        poetry \
        pyflakes \
        pygments \
        pylint \
        requests \
        scikit-learn \
        scipy \
        seaborn \
        uvicorn \
        yapf &&\
    : "clean cache" &&\
    conda build purge-all

# Docker build failed
#
# (Deprecated) Installing extensions with the jupyter labextension install command is now deprecated and will be removed in a future major version of JupyterLab.
# Users should manage prebuilt extensions with package managers like pip and conda, and extension authors are encouraged to distribute their extensions as prebuilt packages
#
# RUN source /etc/profile.d/conda.sh &&\
#     conda activate &&\
#     jupyter labextension install @lckr/jupyterlab_variableinspector@3.0.7

USER u1and0
CMD ["/bin/bash", "-c", "source /etc/profile.d/conda.sh && conda activate && exec bash"]
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
      build_version="python:v1.2.1"
