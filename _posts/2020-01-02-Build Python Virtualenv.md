---
title: "Build Virtualenv"
date: 2020-01-02
categories: Build tools
---

### 1. 파이썬 / pip 설정

* python 설치 후, 다음 실행 (python version 3.6.8 기준)
> <img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/python install.png" width="50%" />

* pip config 파일 및 업그레이드

```
Admins-MacBook-Pro:~ subinkim$ which pip3
/usr/local/bin/pip3
Admins-MacBook-Pro:~ subinkim$ ls /usr/local/bin/pip3
/usr/local/bin/pip3
Admins-MacBook-Pro:~ subinkim$ ls /usr/local/bin/pip3/
/usr/local/bin/pip3/
Admins-MacBook-Pro:~ subinkim$ ls /usr/local/bin/
/////////// 출력 생략 ///////////
pip2				xzgrep
pip2.7				xzless
pip3				xzmore
pip3.6				yamllint
pip3.7
Admins-MacBook-Pro:~ subinkim$ mkdir .config/pip
Admins-MacBook-Pro:~ subinkim$ cd .config/pip
Admins-MacBook-Pro:pip subinkim$ ls
Admins-MacBook-Pro:pip subinkim$ vim
```

```
Admins-MacBook-Pro:pip subinkim$ vim
Admins-MacBook-Pro:pip subinkim$ vim pip.conf 
Admins-MacBook-Pro:pip subinkim$ pip3 list
Package    Version
---------- -------
pip        18.1   
setuptools 40.6.2 
You are using pip version 18
```

```
Admins-MacBook-Pro:pip subinkim$ pip3 install --upgrade pip
Looking in indexes: https://pypi.python.org/simple/
Collecting pip
  Downloading https://files.pythonhosted.org/packages/00/b6/9cfa56b4081ad13874b0c6f96af8ce16cfbc1cb06bedf8e9164ce5551ec1/pip-19.3.1-py2.py3-none-any.whl (1.4MB)
    100% |████████████████████████████████| 1.4MB 13.5MB/s 
Installing collected packages: pip
  Found existing installation: pip 18.1
    Uninstalling pip-18.1:
      Successfully uninstalled pip-18.1
Successfully installed pip-19.3.1
```

### 2. virtualenv 설치 및 진입 

[ 참고링크 ] : https://dgkim5360.tistory.com/entry/python-virtualenv-on-linux-ubuntu-and-windows

```
$ python -m virtualenv venv
$ source venv/bin/activate
```
> 화면 예시

> <img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/install virtualenv.png" width=70%></img>
> <img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/get virtualenv.png" width=70%></img>

* 가상환경 벗어나기

```
$ deactivate
```
> 화면 예시 : 터미널에서 보면, (venv) 상태 제거

> <img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/deactivate virtual.png" width=70%></img>
