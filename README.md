# SGB-IT-Mod-Template
.IT tracker module template for making Super Game Boy music, with the goal of targeting SGB/SGB2's built-in instrument library.

# ⚠ EARLY VERSION, INCOMPLETE ⚠
This project is in its infancy! I hope that by sharing this project, it can provide a starting point towards achieving the goal of aiding developers implement Super Game Boy features in their Game Boy projects.

## Current Features
- All samples ripped from Super Game Boy .SPC files, with loop points intact.
- All instruments are mapped to their respective samples, all with simple placeholder envelopes.     

## TODO, Please Note
- All instruments currently lack envelopes.
- Sample tuning and keys are very likely to be incorrect when compared to SGB/SGB2 instruments on original hardware.
- The actual process of converting .IT to N-SPC data that is compatible with Super Game Boy is one big Unknown. 

These issues come down to two reasons:

1. I don't know how to rip ASDR envelopes from the Super Game Boy.
2. I don't know how to transfer original music to the Super Game Boy.

If you're interested in helping this template match the Super Game Boy's built-in instrument library as close as possible, please make updates and/or get in touch!

---

## Instruments `S00` to `S56`

The template's instrument names are based on official documentation.
[<br>Game Boy Programming Manual (Version 1.1)<br>Chapter 7: Super Game Boy Sound (Pages 209 - 211)](https://archive.org/details/GameBoyProgManVer1.1/page/n208/mode/1up)

Naming convention is as follows:
# `S00 SINE: Normal Env`<br>`S40 BRASS 1: Brass 1`

| From Example | Description |
| :-----: | :---------: |
| "**S00**"<br>"**S40**" | Kankichi-kun Source data Number |
| "**SINE**"<br>"**BRASS 1**" | Sound Family |
| "**Normal Env**"<br><br>"**Brass 1**" | Envelope Type<br>OR<br>Specific Sound |

### "Envelope Type OR Specific Sound"? Why both?
This field description came straight from the programming manual, adding an unavoidable complication to the naming scheme. I've done my best to mitigate confusion.

The manual features a number of envelopes that appear to be reused over multiple instruments. I've made sure every instrument with a shared Envelope Type is given the suffix "Env". These are:

| Envelope Type in Manual | Name in Template |
| --- | --- |
| Banjo envelope | Banjo Env |
| Bass envelope | Bass Env |
| Fretless bass envelope | Fretless Env |
| Brass envelope | Brass Env |
| Electric keyboard envelope | E. Key Env |
| Electric keyboard 1 | E. Key 1 Env |
| Pedal organ envelope | Organ Env |
| Envelope with extremely short decay | Short Decay Env |
| 'Soft' envelope | Soft Env |
| Strings envelope | Strings Env |

If a name in this field is *not* followed by "Env", it can be safely treated as a Specific Sound. 

---

## Instruments `39h` to `3Eh`

There's a group of instruments at the end of the instrument list with the following naming convention:

# `39h: Jet`<br>`3Eh: Wind Blowing`

These are named for their "source data" number in hexadecimal, and the specific sounds they represent. To quote [the manual, page 211](https://archive.org/details/GameBoyProgManVer1.1/page/n210/mode/1up):

> Settings for source data numbers 39h-3Eh cannot be specified on Kankichi-kun. These source data can be used only with sound effects. However, they can be set using tools other than Kankichi-kun.

I'm unsure if these instruments would be usable with N-SPC data uploaded via VRAM transfer, so I would recommend **avoiding** these instruments in music projects until the ability to access them can be confirmed. However, they remain included in the template file in the meantime, as it is important that they be tested for potential use.

--- 

## Samples `000h` to `03Eh`

If for any reason Hexadecimal IDs for source data are required, I recommend referencing the [Game Boy Programming Manual (Version 1.1), Chapter 7: Super Game Boy Sound (Pages 209 - 211)](https://archive.org/details/GameBoyProgManVer1.1/page/n208/mode/1up). However, these are also included in the sample names themselves.

            Source Data
                vv
    "SGB - S00 000h - LOOP Sine"
    "SGB - S12 00Ch - LOOP Bass 2"
    "SGB - S23 017h - LOOP Electric Keyboard 1d"

---

## Changelog

	2023-04-30  v0.01
	Initial version compiled by Lollie (lollie.me)
	- All samples present
	- All instruments present
	- TODO: Envelopes not yet implemented, unable to test SGB hardware
	- TODO: Tuning for all instruments likely do not match SGB hardware
	- TODO: Convert .IT to N-SPC and transfer to SGB *without* samples

---

## Links

Samples extracted from .SPC rips for Super Game Boy using SPLIT700.<br>
.SPC Source: [https://www.zophar.net/music/nintendo-snes-spc/super-gameboy-2](https://www.zophar.net/music/nintendo-snes-spc/super-gameboy-2)<br>
SPLIT700: [https://github.com/gocha/split700](https://github.com/gocha/split700)

Compiled with hopes of targeting mITroid for conversion to N-SPC data.<br>
mITroid: [https://github.com/tewtal/mITroid](https://github.com/tewtal/mITroid)
