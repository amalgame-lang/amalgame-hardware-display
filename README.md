# amalgame-hardware-display

Portable **display drivers** for Amalgame over [`amalgame-hal`](https://github.com/amalgame-lang/amalgame-hal). v0.1 ships the SSD1306 128×64 mono OLED (I²C) — the most common hobby display. One driver, runs on Raspberry Pi and future MCU backends.

```sh
amc package add hardware-display
```

```amalgame
import Amalgame.Hardware          // I2c (Pi backend)
import Amalgame.Hardware.Display

let oled = new Ssd1306(new I2c(1), 0x3C)
oled.Begin()
oled.Clear()
oled.Text(0, 0, "T:23.5C")
oled.HLine(0, 10, 96)
oled.Rect(0, 16, 40, 20)
oled.Show()
```

| Class | API |
|---|---|
| `Ssd1306(bus: I2cBus, addr)` | `Begin()`, `Clear()`, `Pixel(x,y,on)`, `HLine/VLine/Rect`, `Text(x,y,s)`, `Show()` |

The bundled `Font5x7` covers digits, space and common readout symbols/letters; full ASCII is a follow-up. Requires amc ≥ 0.8.72. Apache-2.0.
