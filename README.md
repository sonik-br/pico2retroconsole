# pico2retroconsole
Direct RP2040 GPIO encoder to retro consoles<br/>
Work-in-progress.

This was made with the intention of DIY arcade controller to retro consoles.<br/>
Digital input only. I might add analog input in the future, so a full gamepad could also be made.

Buttons must be wired to GND.<br/>
Firmware is for RP2040 Pi Pico only.

If you're looking to use USB devices on retro consoles, check out my other project:
[usb2retroconsole](https://github.com/sonik-br/usb2retroconsole-fw).

Advice:
- NEVER connect it to the console and to a usb host/device at the same time.
- Connect the encoder to the console while the console is still powered off.

Firmware and wiring directions are provided to you 'as is' and without any warranties. Use at your own risk.

Some encoders will also output over usb when connected to a PC.
Button data maps directly from the GPIO state. Handy for debugging. Also makes it compatible with retro console and PC (never connect to both at the same time!).

There's encoders for: <br/>
- ~~Nes~~
- [Snes](#snes-encoder)
- [Megadrive](#megadrive-encoder)
- [Saturn](#saturn-encoder)
- [PSX](#psx-encoder)
- ~~Jaguar~~

## SNES Encoder

Pico to console

| SNES     | GPIO | Other                     |
|----------|------|---------------------------|
| 1 - VCC  | VBUS |                           |
| 2 - CLK  | 0    |                           |
| 3 - LAT  | 1    |                           |
| 4 - DAT1 | 2    |                           |
| 5 - DAT2 | N/C  |                           |
| 6 - SEL  | 6    | **Optional / for rumble** |
| 7 - GND  | GND  |                           |

| 1 2 3 4 | 5 6 7 )

**All data pins must be level shifted!**<br/>
Pico's GPIO runs at 3.3v and snes runs at 5v.

Buttons to Pico

| GPIO | SNES   |
|------|--------|
| 9    | PAD_U  |
| 10   | PAD_D  |
| 11   | PAD_L  |
| 12   | PAD_R  |
| 13   | B      |
| 14   | Y      |
| 15   | A      |
| 16   | X      |
| 17   | SELECT |
| 18   | START  |
| 19   | L      |
| 20   | R      |

#### Layout

START+L (Default)
<table>
  <tr>
    <td>Y</td>
    <td>X</td>
    <td>L</td>
  </tr>
  <tr>
    <td>B</td>
    <td>A</td>
    <td>R</td>
  </tr>
</table>

START+R
<table>
  <tr>
    <td>B</td>
    <td>A</td>
    <td>R</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>X</td>
    <td>L</td>
  </tr>
</table>

START+Y
<table>
  <tr>
    <td>L</td>
    <td>X</td>
    <td>R</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>B</td>
    <td>A</td>
  </tr>
</table>

START+A
<table>
  <tr>
    <td>B</td>
    <td>A</td>
    <td>X</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>L</td>
    <td>R</td>
  </tr>
</table>

START+X
<table>
  <tr>
    <td>X</td>
    <td>L</td>
    <td>R</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>B</td>
    <td>A</td>
  </tr>
</table>

#### Turbo
Hold SELECT and press A, B, X, Y, L or R to enable/disable turbo for that button.<br/>
Turbo is single frequency only for now. More options are planned for the future.


## Megadrive Encoder

Pico to console

| MegaDrive | GPIO |
|-----------|------|
| D0        | 0    |
| D1        | 1    |
| D2        | 2    |
| D3        | 3    |
| TL        | 4    |
| TR        | 5    |
| TH        | 6    |
| VCC       | VBUS |
| GND       | GND  |

**All data pins must be level shifted!**<br/>
Pico's GPIO runs at 3.3v and megadrive runs at 5v.

Buttons to Pico

| GPIO | MegaDrive |
|------|-----------|
| 9    | PAD_U     |
| 10   | PAD_D     |
| 11   | PAD_L     |
| 12   | PAD_R     |
| 13   | A         |
| 14   | B         |
| 15   | C         |
| 16   | X         |
| 17   | Y         |
| 18   | Z         |
| 19   | START     |
| 20   | MODE      |

#### Mode and Layout

MODE+PAD_U (6 Button pad) (Default)
<table>
  <tr>
    <td>X</td>
    <td>Y</td>
    <td>Z</td>
  </tr>
  <tr>
    <td>A</td>
    <td>B</td>
    <td>C</td>
  </tr>
</table>

MODE+PAD_L (6 Button pad)
<table>
  <tr>
    <td>A</td>
    <td>B</td>
    <td>C</td>
  </tr>
  <tr>
    <td>X</td>
    <td>Y</td>
    <td>Z</td>
  </tr>
</table>

MODE+PAD_D (3 Button pad)
<table>
  <tr>
    <td>-</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>A</td>
    <td>B</td>
    <td>C</td>
  </tr>
</table>

#### Turbo
Hold SELECT and press A, B, C, X, Y or Z to enable/disable turbo for that button.<br/>
Turbo is single frequency only for now. More options are planned for the future.


## Saturn Encoder

Pico to console

| Saturn | GPIO |
|--------|------|
| D0     | 0    |
| D1     | 1    |
| D2     | 2    |
| D3     | 3    |
| TL     | 4    |
| TR     | 5    |
| TH     | 6    |
| VCC    | VBUS |
| GND    | GND  |

**All data pins must be level shifted!**<br/>
Pico's GPIO runs at 3.3v and saturn runs at 5v.

Buttons to Pico

| GPIO | Saturn |
|------|--------|
| 9    | PAD_U  |
| 10   | PAD_D  |
| 11   | PAD_L  |
| 12   | PAD_R  |
| 13   | A      |
| 14   | B      |
| 15   | C      |
| 16   | X      |
| 17   | Y      |
| 18   | Z      |
| 19   | L      |
| 20   | R      |
| 21   | START  |


## PSX Encoder

Pico to console

| PSX      | GPIO |
|----------|------|
| 1 - DAT  | 11   |
| 2 - CMD  | 12   |
| 3 - 9V   | N/C  |
| 4 - GND  | GND  |
| 5 - 3.3V | VBUS |
| 6 - ATT  | 21   |
| 7 - CLK  | 10   |
| 8 - INT  | N/C  |
| 9 - ACK  | 22   |

Do not connect it to a multitap.<br/>
It should work on PS1 and PS2 consoles. But was only tested on PS2.<br/>
It might be incompatible with memorycards on PS1 if connected to the same input port. Be advised that card data corruption might happen.

Buttons to Pico

| GPIO | PSX    |
|------|--------|
| 0    | PAD_U  |
| 1    | PAD_D  |
| 2    | PAD_L  |
| 3    | PAD_R  |
| 4    | X      |
| 5    | ()     |
| 6    | []     |
| 7    | /\     |
| 8    | SELECT |
| 9    | START  |
| 13   | L1     |
| 14   | R1     |
| 15   | L2     |
| 16   | R2     |
| 17   | L3     |
| 18   | R3     |
