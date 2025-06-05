# Neovim container
# *Using my dotfiles
# *Get plugins by dein
# * Inherit from u1and0/archlinux <- archlinux/base
#
# Usage:
#    $ docker pull u1and0/neovim
#    $ docker run -it --rm -v `pwd`:/work -w /work u1and0/neovim nvim [filenames] ...

FROM u1and0/archlinux:latest

USER root
RUN pacman -Sy --noconfirm archlinux-keyring

# Neovim install
RUN pacman -Syyu --noconfirm neovim\
                        python-neovim\
                        vim\
                        fd\
                        fzf\
                        ripgrep\ 
                        w3m\
                        pygmentize\
                        ctags\
                        global \
                        man \
                        npm \
                        jq &&\
    : "'man-pages-ja' not accessible yet 2023.12.29" &&\
    : "Remove all packages cache " &&\
    pacman -Scc --noconfirm

# Plugins insall
# Install & Update plguins & vimproc
USER u1and0
RUN nvim +UpdateRemotePlugins +VimProcInstall +q

# textlint setting
USER root
RUN npm install --global \
        textlint \
        textlint-rule-max-ten \
        textlint-rule-spellcheck-tech-word \
        textlint-rule-preset-japanese \
        textlint-rule-no-mix-dearu-desumasu
USER u1and0

LABEL maintainer="u1and0"\
      description="OS=archlinux, editor=neovim, dotfiles=u1and0/dotfiles, plugin manager=dein"\
      version="neovim:v7.0.0"
