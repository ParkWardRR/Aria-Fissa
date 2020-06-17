This tutorial will walk you through the process of configuring your NodeMCU v3 board for compatablity with a MQTT server

## Ingredients
 - MH-Z19 sensor - [Link](https://esphome.io/components/sensor/mhz19.html)
 -  Microcontroller - NodeMCU v3 - [Link](https://docs.zerynth.com/latest/official/board.zerynth.nodemcu3/docs/index.html) 
	- Be cautious as many sellers are selling other ESP8266 boards in place of the  
	- The Aria Fissa PCB might be compatible with other ESP8266  board. Verify the dimentions, pin count, and the RX/TX pin locations 
- Host - You'll need a [MQTT broker](https://en.wikipedia.org/wiki/MQTT#MQTT_broker)
	- [Eclipse Mosquitto](https://mosquitto.org/) is a popular project  
- Computer to configure the board and your host 
- Soldering iron, solder, flux, and other hobbiest tools/consumables

### Downloads
- [ESPEasy](https://github.com/letscontrolit/ESPEasy/releases) firmware 
	- Look for `espeasy_esp82xx_mega-xxxxxxxxx.zip`

## Warning
The following tutorial will wipe all of the contents of your NodeMCU board.

## Tutorial

 1. Configure and test your serial bootloader utility for your ESP8266
    board  
    - I will be using
    [esptool.py](https://github.com/espressif/esptool) for this tutorial
   2. Connect your ESP8266/NodeMCU to your computer and identify the serial com port
	   - Here is a useful tutorial - [link](mathworks.com/help/supportpkg/arduinoio/ug/find-arduino-port-on-windows-mac-and-linux.html)
	   - For my Mac the nodeMCU v3 is listed as `/dev/tty.SLAB_USBtoUART`
   3. Run the following command to clear the existing bootloader/code/config: 
	   - `esptool.py  --port /dev/tty.SLAB_USBtoUART erase_flash`
	   - Replace `/dev/tty.SLAB_USBtoUART` with the appropriate COM port
   4. Flash the ESPEasy firmware using esptool.py 
	   - The nodemcu v3 board has 4mb of storage and is compatible with most of the ESPEasy packages
	   -  `esptool.py --port /dev/tty.SLAB_USBtoUART write_flash 0x00000 ESP_Easy_mega_20200608_dev_ESP8266_4M1M.bin`
	   -  Once the flash process is complete - disconnect 
   5. 
