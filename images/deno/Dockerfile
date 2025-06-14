# Usage:
# docker run -it --rm -v `pwd`:/work -w /work u1and0/deno

FROM u1and0/zplug:latest

USER root
# Install nodejs, npm, deno, typescript
RUN pacman -Syu --noconfirm nodejs npm &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns &&\
    npm install -g typescript &&\
    curl -fsSL https://deno.land/install.sh | sh
# > The startup time of the Deno command gets affected if it's installed via npm. We recommend the shell install script for better performance.
# https://docs.deno.com/runtime/getting_started/installation/

USER u1and0

LABEL maintainer="u1and0"\
      description="deno / typescript env with neovim"\
      version="deno:v0.1.0"
