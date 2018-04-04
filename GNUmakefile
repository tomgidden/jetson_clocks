# Ref:
# http://www.jetsonhacks.com/2017/03/25/nvpmodel-nvidia-jetson-tx2-development-kit/
# https://devblogs.nvidia.com/jetson-tx2-delivers-twice-intelligence-edge/
# https://elinux.org/Jetson/Performance#Viewing_the_current_CPU_status

default:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/default.conf
	@echo
	@echo "Default profile as booted.  Mostly like Max-Q but with all"
	@echo "six CPU cores active.  It might be that it's _meant_ to be"
	@echo "in Max-Q, but someone forgot something."
	@echo
	@echo "* 4 x ARM CPU cores:       1.2 GHz"
	@echo "* 2 x Denver2 CPU cores:   1.2 GHz"
	@echo "* GPU cores:               0.85 GHz"
	@echo

eleven: maxx
ten: maxn
nine: maxp_all
eight: maxp_arm
seven: maxp_denver
six: default
five: maxq

maxp: maxp_all
eco: maxq
idle: maxq

stats:
	sudo /usr/local/sbin/tegrastats

install:
	sudo cp ~nvidia/jetson_clocks.sh ~nvidia/tegrastats /usr/local/sbin
	sudo mkdir /usr/local/etc/jetson_clocks
	sudo cp default GNUmakefile max* /usr/local/etc/jetson_clocks
	ln -s /usr/local/etc/jetson_clocks/GNUmakefile ~

maxx:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxx.conf
	@echo
	@echo "Max-X is running with no limits at all, forced high, "
	@echo "and the fan turned up.  Undocumented, but it's the result"
	@echo "of running jetson_clocks.sh without parameters."
	@echo
	@echo "Best avoided?"
	@echo
	@echo "* 4 x ARM CPU cores:       2.0 GHz"
	@echo "* 2 x Denver2 CPU cores:   2.0 GHz"
	@echo "* GPU cores:               1.3 GHz"
	@echo

maxn:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxn.conf
	@echo
	@echo "Max-N is running with no limits at all, but no minimum either."
	@echo "Okay on occasion, but wasteful. Better to use Max-P."
	@echo
	@echo "* 4 x ARM CPU cores:       2.0 GHz"
	@echo "* 2 x Denver2 CPU cores:   2.0 GHz"
	@echo "* GPU cores:               1.3 GHz"
	@echo

maxq:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxq.conf
	@echo
	@echo "Max-Q is the peak performance efficiency, at 7.5W."
	@echo
	@echo "* 4 x ARM CPU cores:       1.2 GHz"
	@echo "* 2 x Denver2 CPU cores:   disabled"
	@echo "* GPU cores:               0.85 GHz"
	@echo

maxp_all:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxp_all.conf
	@echo
	@echo "Max-P is for high-performance within 15 W."
	@echo "Good for proper GPU work with medium I/O and threading?"
	@echo
	@echo "* 4 x ARM CPU cores:       1.4 GHz"
	@echo "* 2 x Denver2 CPU cores:   1.4 GHz"
	@echo "* GPU core:                1.12 GHz"
	@echo

maxp_arm:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxp_arm.conf
	@echo
	@echo "Max-P-ARM is for high-performance within 15 W."
	@echo "Good for proper GPU work with better CPU, I/O and threading?"
	@echo
	@echo "* 4 x ARM CPU cores:       2.0 GHz"
	@echo "* 2 x Denver2 CPU cores:   disabled"
	@echo "* GPU core:                1.12 GHz"
	@echo

maxp_denver:
	sudo /usr/local/sbin/jetson_clocks.sh --restore /usr/local/etc/jetson_clocks/maxp_denver.conf
	@echo
	@echo "Max-P-Denver is for high-performance within 15 W."
	@echo "Good for proper GPU work with low I/O?"
	@echo
	@echo "* 1 x ARM CPU core:        0.35 GHz (for supervision)"
	@echo "* 3 x ARM CPU cores:       disabled"
	@echo "* 1 x Denver2 CPU core:    2.04 GHz"
	@echo "* 1 x Denver2 CPU core:    disabled"
	@echo "* GPU core:                1.12 GHz"
	@echo



.PHONY: default maxx maxn maxp_all maxp_arm maxp_denver
