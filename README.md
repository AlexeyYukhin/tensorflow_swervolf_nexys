## Install packages

`sudo apt install git cmake ninja-build gperf ccache dfu-util device-tree-compiler wget python python3-pip python3-setuptools python3-tk python3-wheel xz-utils file make gcc gcc-multilib locales tar curl unzip xxd make autoconf g++ flex bison`

## Install Verilator
`git clone https://github.com/verilator/verilator`

`unset VERILATOR_ROOT`

`cd verilator`

`git checkout stable`

`autoconf`

`./configure`

`make -j 4`

`sudo make install`

`cd examples/make_hello_c`

`make`

Just ensure that Hello world example was successfully run

## Clone repo
`git clone https://github.com/AlexeyYukhin/tensorflow_swervolf_nexys`

`git submodule update --init --recursive`

## Install fusesoc
`sudo pip3 install fusesoc`

## Set env for swervolf
`cd tensorflow_swervolf_nexys`

`export WORKSPACE=$(pwd)`

`export SWERVOLF_ROOT=$(pwd)/fusesoc_libraries/Cores-SwerVolf`

## Install west
`cd`

`pip3 install -U west`

`echo 'export PATH=~/.local/bin:"$PATH"' >> ~/.bashrc`

`source ~/.bashrc`
