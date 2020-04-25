# framework-arduino-avr-lgt8fx
framework-arduino-avr-lgt8fx for WAVGAT development in PlatformIO

Board package is taken from https://github.com/dbuezas/lgt8fx (current version lgt8f-1.0.5)

# how to use
Create `myboard.json`, for WAVGAT NANO AVGA328P: `wavgatnano.json`.
```
{
  "build": {
    "core": "lgt8f",
    "extra_flags": "-DARDUINO_AVR_NANO",
    "f_cpu": "16000000L",
    "mcu": "avga328p",
    "variant": "lgt8fx8p"
  },
  "bootloader": {
    "efuse": "0xFD",
    "file": "lgt8fx8p/optiboot_lgt8f328p.hex",
    "hfuse": "0xFF",
    "lock_bits": "0x3F",
    "lfuse": "0xFF",
    "unlock_bits": "0x3F"
  },
  "frameworks": [
    "arduino"
  ],
  "name": "WAVGAT Nano AVGA328P",
  "upload": {
    "maximum_ram_size": 2048,
    "maximum_size": 29696,
    "protocol": "arduino",
    "require_upload_port": true,
    "speed": 57600
  },
  "url": "https://www.arduino.cc/en/Main/ArduinoBoardNano",
  "vendor": "Arduino"
}
```
Put this `json` file in PlatformIO project dir in the folder boards, such that you have the following structure:
```
rootproject\
    .pio\
    .vscode\
    boards\
        wavgatnano.json
    include\
    lib\
    src\
    test\
    platformio.ini
```

<BR>

Add environment in `platformio.ini`
```
[env:wavgatnano]
platform = atmelavr
board = wavgatnano
framework = arduino
framework-package = framework-arduino-avr-lgt8fx @ https://github.com/rick3rt/framework-arduino-avr-lgt8fx.git
upload_protocol = arduino
```