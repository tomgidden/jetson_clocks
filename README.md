# `jetson_clocks`

## Introduction

The NVidia Jetson TX2 dev kit comes with two utilities to control the myriad processors on the TX2 module.

There's the `nvpmodel` utility that recognises various different clock profiles, and allows for custom profiles;
and there's the `jetson_clocks.sh` utility in `~nvidia` that also seems to control the fan too, for a "balls out"
profile. In addition, there's `/sys` that allows manual tweaking.

Documentation of these isn't particularly forthcoming, but includes:

* https://devblogs.nvidia.com/jetson-tx2-delivers-twice-intelligence-edge/
* https://elinux.org/Jetson/Performance#Viewing_the_current_CPU_status
* http://www.jetsonhacks.com/2017/03/25/nvpmodel-nvidia-jetson-tx2-development-kit/

Various terms like "Max-Q", "Max-P" and so forth are bandied around, but these actually feel more like marketing
terms than actual technical distinctions.  For example, the state the Jetson TX2 seems to start up into isn't
the "Max-Q" that it seems to be, but "Max-Q" with the Denver2 cores _also_ active.

So, this repo contains snapshots of the configurations as programmed by `jetson_clocks.sh`, and simple synonyms
to load them.

I've constructed this as a Makefile purely due to laziness, but would welcome its conversion to a proper script.

## Install

Just do `make install`.  It'll copy the `jetson_clocks.sh` and `tegrastats` utilities out of the `nvidia` user's
home directory -- an odd place for them if you ask me -- and put them and itself in `/usr/local/sbin/` with the
configuration files in `/usr/local/etc/jetson_clocks`.

## Using

Either go to `/usr/local/etc/jetson_clocks`, or symlink `ln -s /usr/local/etc/jetson_clocks/GNUmakefile` into your
home directory.

Then:

* `make` :  Resets to the default boot configuration, as far as I can tell
* `make maxx`:  Balls-to-the-wall full performance with fans going.
* `make maxn`:  "No limits", but no _minimums_ either.
* `make maxq`:  Peak performance per watt, apparently.
* `make ...` :  aw hell, just read the Makefile.

In addition, to make things easier:

* `make eleven` is an alias for `make maxx`... probably overworks the processors for no good reason.
* `make ten` is an alias for `make maxn`... probably what you want for "full performance".
* `make nine`, `make eight`, etc. etc.
* `make idle`, `make eco` : quiet time.

## Contributions

Any improvements and corrections are most welcome.
