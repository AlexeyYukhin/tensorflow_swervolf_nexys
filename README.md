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

## Install the RISC-V-specific version of OpenOCD
`cd riscv-openocd`

`./bootstrap`

`./configure --enable-jtag_vpi --enable-ftdi`

`make`

`sudo make install`

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

## Install zephyr
`cd $WORKSPACE`

`west init`

`west config manifest.path fusesoc_libraries/Cores-SwerVolf`

`west update`

`export ZEPHYR_BASE=$WORKSPACE/zephyr`

`cd $ZEPHYR_BASE`

`pip3 install -r scripts/requirements.txt`

## Install zephyr SDK
`wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.12.4/zephyr-sdk-0.12.4-x86_64-linux-setup.run`

`chmod +x zephyr-sdk-0.12.4-x86_64-linux-setup.run`

`./zephyr-sdk-0.12.4-x86_64-linux-setup.run -- -d ~/zephyr-sdk-0.12.4`

## Build Hello World example
`cd $WORKSPACE/tensorflow`

`make -f tensorflow/lite/micro/tools/make/Makefile TERGET=zephyr_swervolf BUILD_TYPE=debug hello_world_bin`

The resulting binaries can be found in the 
`tensorflow/lite/micro/tools/make/gen/zephyr_vexriscv_x86_64/hello_world/build/zephyr` folder.
