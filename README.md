# GreatFET: out of tree example

This is simple, example firmware that builds against the GreatFET codebase without existing in the GreatFET tree. 
It's meant to serve as an example of how one might create a "one-off" firmware for the GreatFET Azalea.

## Usage

External builds traditionally use the `GREATFET_PATH` environment variable to point to the GreatFET repository. With 
that variable defined, you can build this like you would any other GreatFET firmware.

```sh

# Assuming our GreatFET tree is located at ~/greatfet
export GREATFET_PATH=~/greatfet/

# Configure our build...
mkdir build
cd build
cmake ..

# ... build it, and program the result to a GreatFET Azalea in DFU mode.
make -j5 blinky_external-program
```
