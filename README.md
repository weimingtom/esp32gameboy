# esp32gameboy
<center><img src="https://github.com/rpsubc8/esp32gameboy/blob/master/preview/preview.jpg"></center>
Gameboy emulate ESP32
<ul>
 <li><b>fabgl:</b> sound, vga, keyboard and 4 bank cache</li>
 <li><b>vga32:</b> vga, keyboard and 8 bank cache</li>
</ul> 

<ul>
 <li>Arduino IDE 1.8.11</li>
 <li>TTGO VGA32 ESP32</li>
 <li>https://dl.espressif.com/dl/package_esp32_index.json</li>
 <li>ESP32 espressif Systems 1.0.4</li>
 <li>Libreria fabgl 0.9.0</li>
 <li>Libreria Bitluini ESP32lib 0.3.3</li>
</ul>

<pre>
 #define lib_compile_fabgl
 //#define lib_compile_vga32
 
 //user_min_ram - min ram consume, not bank cache
 #define use_max_ram
</pre>

We have to comment and decomment the library options we want to use, as well as the RAM consumption.

A version is available and it can be climbed with the esptools of the Arduino:

https://github.com/rpsubc8/esp32gameboy/blob/master/arduino/hex/hex.zip

Example:

<pre>
f:\Users\AppData\Local\Arduino15\packages\esp32\tools\esptool_py\2.6.1/esptool.exe --chip esp32 --port COM44 --baud 921600 --before default_reset --after hard_reset write_flash -z --flash_mode dio --flash_freq 80m --flash_size detect 0xe000 f:\Users\AppData\Local\Arduino15\packages\esp32\hardware\esp32\1.0.4/tools/partitions/boot_app0.bin 0x1000 f:\Users\AppData\Local\Arduino15\packages\esp32\hardware\esp32\1.0.4/tools/sdk/bin/bootloader_qio_80m.bin 0x10000 v:\Temp\arduino_build_211050/gameboy.ino.bin 0x8000 v:\Temp\arduino_build_211050/gameboy.ino.partitions.bin 
</pre>

The directories should be replaced by ours, as well as the COM port and speed.

Tool to generate struct 10 roms .h:

https://github.com/rpsubc8/esp32gameboy/tree/master/arduino/tools

The roms .gb must be introduced in the directory rom, and when launching:
<pre>
 rom2h roms
</pre>
All the .h that we must drop in the project will be generated.
