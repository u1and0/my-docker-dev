# zsh/zplug container
# * zshell powered by zplug
# * Using my dotfiles
# * Inherit from u1and0/neovim <- u1and0/archlinux <- archlinux/base
#
# Usage:
#    $ docker pull u1and0/zplug
#    $ docker run -it --rm -v `pwd`:/work -w /work u1and0/zplug

FROM u1and0/neovim:latest

# Reinstall packages required by zplug
USER root
RUN pacman -Sy --noconfirm archlinux-keyring &&\
    pacman -Syyu --noconfirm zsh awk bat actionlint unzip eza diff-so-fancy npm &&\
    : "pacmanのキャッシュ削除"&&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns

# git-flow install for git work flow
WORKDIR /tmp
RUN curl --silent --location  https://raw.githubusercontent.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh --output ./gitflow-installer.sh &&\
    bash gitflow-installer.sh install stable &&\
    rm gitflow-installer.sh

# Install gpt-cli
RUN latest_url=$(curl -s https://api.github.com/repos/u1and0/gpt-cli/releases/latest \
    | grep "browser_download_url.*gpt-cli-linux-x64.zip" \
    | cut -d '"' -f 4) &&\
    curl -fsSLO $latest_url &&\
    unzip gpt-cli-linux-x64.zip &&\
    chmod 755 release-package/gpt &&\
    mv release-package/gpt /usr/bin

# Install Agents cli
RUN npm install -g @google/gemini-cli \
    @qwen-code/qwen-code \
    @anthropic-ai/claude-code

# Install zplug plugins
# zplug install でエラー
#0 2.539 [zplug] WARNING: pipe syntax is deprecated! Please use 'on' tag instead.
# 解決策がわからないのでとりあえず`|| exit0`
USER u1and0
WORKDIR /home/u1and0
RUN git clone --depth 1 https://github.com/zplug/zplug .zplug &&\
    zsh -ic "source .zshrc && zplug install" || exit 0
ENV SHELL="/usr/bin/zsh"
CMD ["/usr/bin/zsh"]

LABEL maintainer="u1and0"\
      description="OS=archlinux editor=neovim shell=zsh_with_zplug"\
      version="zplug v7.0.0"
