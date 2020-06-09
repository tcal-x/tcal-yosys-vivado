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
./receiver.py --port /dev/ttyUSB1 --baud 500000 --verbose 0
```
(You may need to do `pip install pyserial`.)


To see the raw data stream:

```
lxterm --speed 500000 /dev/ttyUSB1
```
...or something similar.

### Malfunction on HW

If you run the receiver.py script, it will just get stuck and show some small number of 000000.

If you look at the raw data stream using lxterm, it will be lines of 16 zeros `0000000000000000`.

You _should_ instead be seeing non-zero hexadecimal values in the raw stream.  The `receiver.py` script
should say something like "Five matching values.  Have sync.".

You can easily compile this design with a 100% Vivado flow, using all of the `.v` files as sources, and `arty.xdc` as the constraint file.   With Vivado compilation, you will get correct behavior.


