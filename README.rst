The Zephyr Project is a scalable real-time operating system (RTOS) supporting
multiple hardware architectures, optimized for resource constrained devices,
and built with security in mind.

The Zephyr OS is based on a small-footprint kernel designed for use on
resource-constrained systems: from simple embedded environmental sensors and
LED wearables to sophisticated smart watches and IoT wireless gateways.

The Zephyr kernel supports multiple architectures, including ARM Cortex-M,
Intel x86, ARC, Nios II, Tensilica Xtensa, and RISC-V, and a large number of
`supported boards`_.

* **Documentation**: http://docs.zephyrproject.org

## Launch

```shell
sudo apt install --no-install-recommends git cmake ninja-build gperf \
  ccache dfu-util device-tree-compiler wget \
  python3-dev python3-pip python3-setuptools python3-tk python3-wheel xz-util$
  make gcc gcc-multilib g++-multilib libsdl2-dev

pip3 install --user -U west

echo 'export PATH=~/.local/bin:"$PATH"' >> ~/.bashrc
source ~/.bashrc

west init $HOME/projects/zephyr/zephyrproject
cd $HOME/projects/zephyr/zephyrproject
west update

west zephyr-export

pip3 install --user -r ~/zephyrproject/zephyr/scripts/requirements.txt


cd $HOME/Downloads/
wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.12.0-a$

chmod +x zephyr-sdk-0.12.0-alpha-1-x86_64-linux-setup.run
./zephyr-sdk-0.12.0-alpha-1-x86_64-linux-setup.run -- -d ~/zephyr-sdk-0.12.0

sudo cp ~/zephyr-sdk-0.12.0/sysroots/x86_64-pokysdk-linux/usr/share/openocd/c$
sudo udevadm control --reload

west build -p auto -b gr716a_mini samples/basic/blinky
```

