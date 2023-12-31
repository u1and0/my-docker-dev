Dockerfile for [u1and0/go](http://hub.docker.com/r/u1and0/go)

![screen](https://raw.githubusercontent.com/u1and0/docker_vim-go/screenshot/Screenshot%20from%202019-01-27%2020-42-18.png)


# Install & Run

```
docker pull u1and0/go
docker run -it --rm -v `pwd`:/work -w /work u1and0/go
```


# Description
* `go version` => go1.11.5 linux/amd64
* Neovimコンテナベース([u1and0/neovim](http://hub.docker.com/r/u1and0/archlinux))
* `python-neovim` インストール済み
  * `nvim --version`

    ```
    NVIM v0.3.4
    Build type: Release
    LuaJIT 2.0.5
    Compilation: /usr/bin/cc -march=x86-64 -mtune=generic -O2 -pipe -fstack-protector-strong -fno-plt -Wconversion -O2 -DNDEBUG -DMIN_LOG_LEVEL=3 -Wall -Wextra -pedantic -Wno-unused-parameter -Wstrict-prototypes -std=gnu99 -Wimplicit-fallthrough -Wvla -fstack-protector-strong -fdiagnostics-color=auto -Wno-array-bounds -DINCLUDE_GENERATED_DECLARATIONS -D_GNU_SOURCE -DNVIM_MSGPACK_HAS_FLOAT32 -DNVIM_UNIBI_HAS_VAR_FROM -I/build/neovim/src/build/config -I/build/neovim/src/neovim-0.3.4/src -I/usr/include -I/build/neovim/src/build/src/nvim/auto -I/build/neovim/src/build/include
    Compiled by builduser

    Features: +acl +iconv +jemalloc +tui
    See ":help feature-compile"

          システム vimrc: "$VIM/sysinit.vim"
           省略時の $VIM: "/usr/share/nvim"

    Run :checkhealth for more info
    ```

* <kbd>C-Z</kbd>によるsuspendは無効化してあるので、代わりにdockerのdetach<kbd>C-P</kbd><kbd>C-Q</kbd>を使う
* プラグインインストール済み(詳細は[u1and0/dotfiles](https://github.com/u1and0/dotfiles/tree/master/.config/dein))
    * fatih/vim-go
    * zchee/deoplete-go
    * go, gocode, その他`:GoBinaries`で手に入るバイナリ取得済み


# Version
* v2.1.0          [mod] rebuild from u1and0/zplug:v5.1.0
* v2.0.0          [mod] from u1and0/archlinux user u1and0
* v1.3.0          [add] go REPL(gore) & ghq (package manager)
* v1.2.0          [mod] ENTRYPOINT nvim -> bash for restart nvim
* v1.1.0          [mod] remove /root/go/src after building
* v1.0.0          ditfiles version v1.13.3 + Neovim

