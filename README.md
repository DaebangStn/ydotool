# ydotool [![Build Status](https://github.com/ReimuNotMoe/ydotool/workflows/Build/badge.svg)](https://github.com/ReimuNotMoe/ydotool/actions/workflows/push_pr_build_cmake.yml) [![Release Status](https://github.com/ReimuNotMoe/ydotool/workflows/Release/badge.svg)](https://github.com/ReimuNotMoe/ydotool/actions/workflows/release_cmake.yml)

Generic Linux command-line automation tool (no X!)

**`ydotool` is not limited to Wayland.** You can use it on anything as long as it accepts keyboard/mouse/whatever input. For example, X11, text console, "RetroArch OS", fbdev apps (fbterm/mplayer/SDL1/LittleVGL/Qt Embedded), etc.

## Build
**CMake 3.22+ is required.**

### Build options
There are a few extra options that can be configured when running CMake

- BUILD_DOCS=ON|OFF - whether to build the documentation, depends on ``scdoc``. Default: ON
- SYSTEMD_USER_SERVICE=ON|OFF - whether to use systemd user service file, depends on ``systemd``. Default: ON
- SYSTEMD_SYSTEM_SERVICE=ON|OFF - whether to use systemd system service file, depends on ``systemd``. Default: OFF
- OPENRC=ON|OFF - whether to use openrc service file. Default: OFF (TBD)


### Compile

<pre><code>
git clone https://github.com/ReimuNotMoe/ydotool
cd ydotool
mkdir build
cd build
cmake -DSYSTEMD_SYSTEM_SERVICE=ON -DSYSTEMD_USER_SERVICE=OFF ..
make -j `nproc`
sudo ln -s $(pwd)/ydotool /usr/local/bin/ydotool
sudo ln -s $(pwd)/ydotoold /usr/local/bin/ydotoold
sudo cp ./ydotoold.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable ydotoold.service # later changed to ydotool.service
sudo systemctl start ydotoold.service
</code></pre>
