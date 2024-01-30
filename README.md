<img src="https://github.com/u1and0/my-docker-dev/actions/workflows/docker-image.yml/badge.svg"></img>
<img src="https://img.shields.io/badge/LICENSE-MIT-3388FF.svg"></img>

# What for
docker in docker dev.env

* master: zsh & zplug env. Parents for all docker image.
* go: golang env.
* deno: JavaScript runtime Deno env.
* Python: Python env. Develop on ipython & jupyter lab

# Usage

```
$ git clone u1and0/my-docker-dev
$ cd /path/to/my-docker-dev
$ docker-compose up
$ docker exec -it my-docker-dev_master_1 zsh -l

# Login master container then...
$ tmux

# Login go env
$ docker exec -it my-docker-dev_go_1 zsh -l

# Login deno env
$ docker exec -it my-docker-dev_deno_1 zsh -l

# Login python env
$ docker exec -it my-docker-dev_jupyter_1 zsh

# Login ipython
$ docker exec -it my-docker-dev_jupyter_1 bash -c "source /etc/profile.d/conda.sh && conda activate && ipython"

# Run jupyter lab
$ docker exec -it my-docker-dev_jupyter_1 bash -c "source /etc/profile.d/conda.sh && conda activate && jupyter lab"
```
