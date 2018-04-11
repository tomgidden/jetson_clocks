install:
	sudo mkdir -p /usr/local/sbin
	sudo cp ~nvidia/jetson_clocks.sh ~nvidia/tegrastats /usr/local/sbin
	sudo cp jetson_clocks /usr/local/sbin
	sudo chmod 755 /usr/local/sbin/jetson_clocks
	sudo mkdir -p /usr/local/etc/jetson_clocks
	sudo cp *.conf /usr/local/etc/jetson_clocks
	sudo cp sudoers.d__jetsonclocks /etc/sudoers.d/
	sudo chmod 440 /etc/sudoers.d/sudoers.d__jetsonclocks

clean:
	sudo rm /usr/local/sbin/jetson_clocks{,.sh}
	sudo rm /usr/local/etc/jetson_clocks/*.conf
	sudo rmdir /usr/local/etc/jetson_clocks
