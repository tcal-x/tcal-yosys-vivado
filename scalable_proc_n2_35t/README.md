# Simple Yosys -> Vivado example (with Edalize)

## Prepare the environment

If this is the first time you're building one of these examples, install prerequisites and prepare the env (otherwise skip to 'Build the example').


### Install prerequisites



```
sudo pip install virtualenv
```

Install Yosys following the guide from https://github.com/YosysHQ/yosys#setup
Install Vivado following the guide from https://www.xilinx.com/products/design-tools/vivado.html

### Prepare env

```
virtualenv env
source env/bin/activate
pip install edalize
```

## Build the example
In this directory:

```
python3 yosys-vivado.py
```

The above instructions assume both Vivado and Yosys are installed and in the PATH. 


## Run the example
After putting the bitstream `./build/design.bit` on your Arty 35T board, test the design over the USB connection:


```
receiver.py --port /dev/ttyUSB1 --baud 500000 --verbose 0
```

To see the raw data stream:

```
lxterm --speed 500000 /dev/ttyUSB1
```
...or something similar.

