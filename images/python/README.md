Welcome to Python dev docker image
---


# Usage
In host machine's shell

```
$ docker pull u1and0/python
$ docker run -it --rm -v `pwd`:/work -w /work u1and0/python
```



## Using other command with activating `conda`

```
$ docker run -it --rm -v `pwd`:/work -w /work\
     u1and0/python bash -c ". .bashrc && python"
$ docker run -it --rm -v `pwd`:/work -w /work\
     u1and0/python bash -c ". .bashrc && ipython"
$ docker run -it --rm -v `pwd`:/work -w /work\
     u1and0/python bash -c ". .bashrc && nvim"
$ docker run -p 8888:8888 -it --rm -v `pwd`:/work -w /work\
     u1and0/python bash -c ". .bashrc && jupyter notebook"
```


## In contaner

Just type

```
$ ipython
   or
$ jupyter notebook
   or
$ nvim
```
