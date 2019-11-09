install:
	sudo mkdir -p /usr/local/sbin
	sudo cp jetson_power /usr/local/sbin
	sudo chmod 755 /usr/local/sbin/jetson_power
	sudo mkdir -p /usr/local/etc/jetson_power
	sudo cp *.conf /usr/local/etc/jetson_power
	sudo cp sudoers.d__jetsonpower /etc/sudoers.d/
	sudo chmod 440 /etc/sudoers.d/sudoers.d__jetsonpower

clean:
	sudo rm /usr/local/sbin/jetson_power
	sudo rm /usr/local/etc/jetson_power/*.conf
	sudo rmdir /usr/local/etc/jetson_power
