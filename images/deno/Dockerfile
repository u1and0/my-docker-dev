# Usage:
# docker run -it --rm -v `pwd`:/work -w /work u1and0/deno

FROM u1and0/zplug:latest

# Copy deno binary from container
# https://docs.deno.com/runtime/getting_started/installation/
# shからのインストールは対話的なコマンドが必要
COPY --from=denoland/deno:latest /usr/bin/deno /usr/bin/deno

USER root
# Install nodejs, npm, deno, typescript
RUN pacman -Syu --noconfirm nodejs npm &&\
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns &&\
    npm install -g typescript

USER u1and0

LABEL maintainer="u1and0"\
      description="deno / typescript env with neovim"
