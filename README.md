
# Gateway MQTT status script

This script sends power and temperature data from a CM4-POE-UPS-BASE  board using MQTT to our cloud server.
Example:

    {"host": "gw-ap2", "temperature": 50.1, "bus_voltage": 4.188, "shunt_voltage": 0.0, "current": -0.0009144000000000001, "power": 0.006096, "p": 98.99999999999997}

## Requirements

- I2C enabled on the raspberry pi:
	To enable I2C on the raspberry pi edit the /boot/config.txt as root
	 - Comment out "dtparam=audio=on" using a #
	 - Add the following lines at the end
		    dtparam=i2c_vc=on
		    dtoverlay=i2c-rtc, pcf85063a, i2c_csi_dsi
	
	A reboot is necessary after these changes
    
- Python3 and packages:
	- smbus
	- paho.mqtt
	- dotenv

## Usage

Copy the .env.default to .env and set the variables to their correct values.
Run the script using `python3 metadata_to_db.py`
For permanent deployment invoke the script using cron

## Credits

This script is an extension from a waveshare script for a CM4-POE-UPS-BASE board.
