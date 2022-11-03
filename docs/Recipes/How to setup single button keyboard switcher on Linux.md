# How to setup single button keyboard switcher on Linux Mint (Cinnamon)

```bash
sudo apt install -y libx11-dev libxkbfile-dev cmake
git clone [git@github.com](mailto:git@github.com):nonpop/xkblayout-state.git && make
cp xkblayout-state ~/scripts && chmod +x ~/scripts/xkblayout-state
git clone git@github.com:grwlf/xkb-switch.git
cd xkb-switch && mkdir build && cd build && cmake .. && make
sudo make install && sudo ldconfig #didn't find another way... =(
```

Then just add `xkb-switch -n` to the custom keymap binding and that's it!

Then create the following script and add it to the customer keyboards layout:

```bash
#!/bin/bash
#Simple script, that enables Mac style keyboard switch with one button - like 'Fn'

#Fail completely on first error
set -e

# gettint current layout
layout=$(~/scripts/xkblayout-state print %s)

# Defining layouts to swap against
english=us
mylayout=ru

# Do simple logical switch here
if [[ $layout == $mylayout ]]; then
setxkbmap -layout $english
else
setxkbmap -layout $mylayout -variant mac
fi
```