# `jetson_power`

## Introduction

The NVidia Jetson TX2 dev kit comes with two utilities to control the
myriad processors on the TX2 module.

There's the `nvpmodel` utility that recognises various different clock
profiles, and allows for custom profiles; and there's the
`jetson_clocks` utility in `/usr/bin` that also seems to control the fan
too, for a "balls out" profile. In addition, there's `/sys` that allows
manual tweaking.

Documentation of these isn't particularly forthcoming, but includes:

* https://devblogs.nvidia.com/jetson-tx2-delivers-twice-intelligence-edge/
* https://elinux.org/Jetson/Performance#Viewing_the_current_CPU_status
* http://www.jetsonhacks.com/2017/03/25/nvpmodel-nvidia-jetson-tx2-development-kit/

Various terms like "Max-Q", "Max-P" and so forth are bandied around, but
these actually feel more like marketing terms than actual technical
distinctions.  For example, the state the Jetson TX2 seems to start up
into isn't the "Max-Q" that it seems to be, but "Max-Q" with the Denver2
cores _also_ active.

So, this repo contains snapshots of the configurations as programmed by
`jetson_clocks`, and simple synonyms to load them.

## Install

Just do `make install`.

## Using

* `jetson_power` :  Resets to the default boot configuration, as far as I can tell
* `jetson_power maxx`:  Balls-to-the-wall full performance with fans going.
* `jetson_power maxn`:  "No limits", but no _minimums_ either.
* `jetson_power maxq`:  Peak performance per watt, apparently.
* `jetson_power ...` :  aw hell, just read the script. It's fairly simple.

In addition, to make things easier:

* `jetson_power eleven` is an alias for `jetson_power maxx`... probably overworks the processors for no good reason.
* `jetson_power ten` is an alias for `jetson_power maxn`... probably what you want for "full performance".
* `jetson_power nine`, `jetson_power eight`, etc. etc.
* `jetson_power idle`, `jetson_power eco` : quiet time.

## Contributions

Any improvements and corrections are most welcome.
