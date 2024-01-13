<img src="https://github.com/u1and0/my-docker-dev/actions/workflows/docker-image.yml/badge.svg"></img>
<img src="https://img.shields.io/badge/LICENSE-MIT-3388FF.svg"></img>

# What for
docker in docker dev.env

* master: zsh & zplug env. Parents for all docker image.
* python: python env. It can use ipython & jupyter
* go: golang env.

# Usage

```
$ cd /path/to/composeset
$ docker-compose up
$ docker exec -it composeset_master_1 zsh -l

# Login master container then...
$ tmux

# Login go env
$ docker exec -it composeset_vim-go_1 zsh -l

# Login python env
$ docker exec -it composeset_jupyter_1 bash -c ". .bashrc && zsh"

# Login python env as ipython
$ docker exec -it composeset_jupyter_1 bash -c ". .bashrc && ipython"
```
