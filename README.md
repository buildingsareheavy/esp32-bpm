# ESP32 BPM Detector

Real-time BPM detector on an ESP32. Early prototype for a handheld tool for vinyl DJs and a larger DJ controller/mixer project.

## Status

- [x] PlatformIO toolchain and upload
- [x] SH1106 OLED on I²C
- [ ] Analog input circuit (3.5 mm jack to ADC)
- [ ] ADC sampling
- [ ] BPM detection
- [ ] BPM on Display 1, source and signal level on Display 2
- [ ] Source select button

## Hardware

- Inland ESP32-WROOM-32E dev board
- Hosyond 1.3" SH1106 128×64 I²C OLED
- Breadboard and jumper wires

## Wiring

| OLED | ESP32  |
| ---- | ------ |
| GND  | GND    |
| VCC  | 3V3    |
| SCK  | GPIO22 |
| SDA  | GPIO21 |

The screen is powered from 3V3. The ESP32's GPIO pins are not 5 V tolerant.

## Build and upload

Requires VS Code with the PlatformIO extension.

1. Open the project folder in VS Code.
2. Select the `esp32dev` environment.
3. Upload with `pio run -t upload`, or use the PlatformIO Upload button.
4. If the upload stalls on "Connecting...", hold the BOOT button.

On Linux, add your user to the `dialout` group to access the serial port:

```
sudo usermod -aG dialout $USER
```

Then log out and back in.

## Layout

- `platformio.ini`: environments and library dependencies
- `src/main.cpp`: firmware entry point

## Roadmap

- Analog input: mix L/R, AC-couple, bias to the ADC midpoint, attenuate, protect
- Beat detection kept separate from hardware code so it can be reused on a Teensy 4.1
- Second display and a button for input source
- Later: mic input, battery power, custom PCB
