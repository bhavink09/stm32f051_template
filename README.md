# STM32f051 Template
This is an example eclipse based blinky project for STM32F051 (ARM Cortex M0 controller). Below are the steps to get it working in Linux (Ubuntu 14.04 and above)

### Installing Eclipse and GNU ARM Toolchain
* Download Eclipse for C/C++ from here: https://eclipse.org/downloads/
* Install the GNU ARM plugins as per the steps mentioned here [Note: Although the link does not mention, you need to install the Packs and Qemu plugins as well]: http://gnuarmeclipse.livius.net/blog/plugins-install/
* Also install and configure the packs plugin as mentioned here: http://gnuarmeclipse.livius.net/blog/packs-manager/#The_Packs_perspective
* Download QEMU binaries from here: http://sourceforge.net/projects/gnuarmeclipse/files/QEMU/GNU%20Linux/

### ARM GCC Toolchain install
* Download the tar file form here: https://launchpad.net/gcc-arm-embedded/+download
* Open the terminal and enter the following command:
``` sh1
$ mkdir ~/ARMTools
$ cd ~/ARMTools
```
* Extract the download file inside this directory:
``` sh2
$ tar -xvf gcc-arm-none-eabi-j_n-yyyyqe-yyyymmdd-linux.tar.bz2
```
* Create symlinks to the binaries. This is required so that we don't have to add the folder path in $PATH variable. This also prevents modifying the eclipse PATH variable.
``` sh3
$ cd /usr/local/bin
$ sudo ln -s /home/${USER}/ARMTools/gcc-arm-none-eabi-j_n-yyyyge-yyyymmdd-linux.tar.bz2/bin/* .
```
### Openocd Install
* Download the openocd src code from here: http://sourceforge.net/projects/openocd/
* Extract the folder into /home/${USER}/ARMTools/
* Build and install from src
``` sh4
$ cd openocd-x.y.z
$ ./configure
$ make
$ sudo make install
```
* Execute the following commands:
``` sh5
$ cd /home/${USER}/ARMTools/
$ tar -xvf openocd-x.y.z.tar.bz2
$ mkdir -p openocd-bin/scripts openocd-bin/bin
$ cp -R openocd-x.y.z/tcl/* openocd-bin/scripts/
$ cd openocd-bin/bin
$ ln -s /usr/local/bin/openocd openocd
```
* Add openocd_path variable to env.
``` sh6
$ echo "export OPENOCD_PATH=/home/bhavin/ARMUtils/openocd-bon/bin" >> .bashrc
```
(For windows, download and install from here: http://sourceforge.net/projects/gnuarmeclipse/files/OpenOCD/Windows/)
