## Docker GCC

### 使用 Docker Container 為開發環境

開發者也可以選擇利用 docker container 為開發環境。
其快速、方便，可大幅提升開發者在開發環境部署上的效率。

### 建立 Docker image

利用 [docker-library/gcc](https://github.com/docker-library/gcc)上面的
dockerfile 來建立 docker image。

```bash
# 首先 clone 該專案至 local 端
$ git clone https://github.com/docker-library/gcc.git

# 進入 gcc/5.1 資料夾
$ cd gcc/5.1

# 開始建立 image
$ docker build -t gcc-5.1 .
```

### 編譯與執行

```bash
# 編譯
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 gcc -o hello hello.c

# 執行
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./hello
```

### 參考文獻

* [docker run 參數](https://docs.docker.com/reference/run/#clean-up-rm)
* [docker library](https://hub.docker.com/_/gcc/)
