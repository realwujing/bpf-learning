# ebpf-learning

## BCC

[BPF Compiler Collection (BCC)](https://github.com/iovisor/bcc.git)

## ubuntu18安装BCC教程

- Install build dependencies

    ```bash
    sudo apt-get -y install bison build-essential cmake flex git libedit-dev \
  libllvm6.0 llvm-6.0-dev libclang-6.0-dev python zlib1g-dev libelf-dev libfl-dev python3-distutils
    ```

- Install and compile BCC

    ```bash
    set -aex
    git clone https://github.com/iovisor/bcc.git
    git checkout v0.24.0
    mkdir bcc/build
    cd bcc/build
    cmake ..
    make
    sudo make install
    cmake -DPYTHON_CMD=python3 .. # build python3 binding
    pushd src/python/
    make
    sudo make install
    popd
    ```

- Environment variable configuration

    ```bash
    echo "export PATH=$PATH:/usr/share/bcc/tools" >> /etc/profile
    ```

    ```text
    sudo visudo后追加/usr/share/bcc/tools到secure_path后面
    Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/usr/share/bcc/tools"
    ```

    ```bash
    source /etc/profile
    ```

- Get started

    ```bash
    sudo execsnoop
    ```

## More

- [https://github.com/iovisor/bcc/blob/master/INSTALL.md#ubuntu---source](https://github.com/iovisor/bcc/blob/master/INSTALL.md#ubuntu---source)
- [解决 sudo 执行命令时找不到命令问题](https://www.cnblogs.com/lfri/p/16277069.html)