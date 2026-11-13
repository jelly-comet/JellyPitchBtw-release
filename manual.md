# JellyPitchBtw manual

**Pitch correction for one voice, steered by a jellyfish.** One puck sets how fast a note is
pulled in and how much of the singing round it is left alone, and a display shows the voice as
sung and as corrected.

Version 1.0.0. To install it, see the [README](README.md).

## Contents

- [Getting started](#getting-started)
- [The controls](#the-controls)
- [How to use it](#how-to-use-it)
- [Good to know](#good-to-know)
- [Troubleshooting](#troubleshooting)

## Getting started

Put JellyPitchBtw on a track with one voice on it: a lead vocal, a backing vocal, a solo
instrument that plays one note at a time. Choose the song's key and scale at the top left, play
the track, and watch the display: the blue line is the voice as sung, the bright line as it comes
out, and each note it is pulled to sits behind them as a bar.

At the defaults (the puck in the middle of the pad) a note is pulled in over 25 ms and half of
the vibrato round it is kept: corrected, but still a singer. Drag the puck towards the bottom
left corner to hear the hard, robotic snap; towards the top right for a correction you barely
notice.

![JellyPitchBtw correcting a sung phrase: the jellyfish pad at the left, the voice as sung and as corrected in the display at the right](images/screenshot.png)

## The controls

From the top left of the window.

| Control | Range | Default | What it does |
| --- | --- | --- | --- |
| **Power switch** (top right) | On / Off | On | Off, the voice passes through uncorrected, as late as the latency the plugin reports, so the track stays in time. |
| **Key and scale** | C to B; 13 scales | C, Chromatic | The notes a voice is pulled to. Chromatic is every note: plain tuning. |
| **REALTIME** | On / Off | On | On: 0.25 ms behind, for singing through it. Off: Quality, a look-ahead that puts each correction on the start of its note, for mixing and bouncing. |
| **The pad: SPEED** (left to right) | 1 to 200 ms | 25 ms | How fast a new note is pulled in. 1 ms snaps; 200 ms glides. |
| **The pad: VIBRATO** (bottom to top) | 0 to 100 % | 50 % | How much of the movement round a note is left alone. 0 % irons it flat; 100 % keeps the vibrato and the scoops as sung. |
| **STRENGTH** (display) | 0 to 100 % | 100 % | How much of the correction is applied. 0 % leaves the pitch as sung. |
| **DETUNE** (display) | −100 to +100 cents | 0 ct | Moves the corrected voice off the note, for a slightly flat or sharp double. |
| **FORMANT** (display) | −12 to +12 semitones | 0.0 st | Moves the voice's formants: down for a darker, bigger voice, up for a smaller, brighter one, without changing the note. |
| **HOLD** (display) | 0 to 100 % | 0 % | How far the formants stay put while the pitch is corrected. Turn it up when a corrected note sounds thinner or chipmunky. |
| **A4** (display) | 415 to 466 Hz | 440.0 Hz | The tuning reference, for a band or a recording tuned off 440. |
| **VOICE** (display) | Low, Normal, High | Normal | Where the voice is looked for: Low 50 to 400 Hz, Normal 80 to 800 Hz, High 150 to 1500 Hz. |
| **Zoom** (top right) | 100 to 200 % | 100 % | The window's size, kept with the project. |

## How to use it

### The pad

The puck's two directions are the two things that make correction sound natural or not.

- **Left and right is SPEED:** how long a new note takes to be pulled in. Fast (left) is the
  stepping, robotic effect; slow (right) lets the singer's own slide into a note through.
- **Up and down is VIBRATO:** how much of the wobble round a note is kept. At the bottom the note
  is held flat; at the top the vibrato and every little move come through as sung.

Press anywhere on the pad and the puck jumps there and follows you; press on the puck itself to
take hold of it where it is. Shift makes a drag ten times finer, and a double-click puts the puck
back in the middle. The values under the pad move on their own: drag one up or down, use the
wheel over it, right-click it to type a value, or double-click to reset it.

The note is always chosen from the centre of what is sung, so a wide vibrato stays on its note
instead of hopping to the neighbour. Settings to start from:

| For | SPEED | VIBRATO |
| --- | --- | --- |
| The hard, stepping effect | 1 ms | 0 % |
| A tight pop vocal | 10 to 25 ms | 30 to 50 % |
| A natural fix you shouldn't hear | 60 to 120 ms | 70 to 100 % |

### REALTIME or Quality

- **REALTIME on** (the default) is for recording or performing: the plugin is 0.25 ms behind
  (12 samples at 48 kHz), too little to feel. A correction follows its note, so the very start of
  a note can be heard sliding in.
- **REALTIME off** is Quality: the plugin looks ahead, 16 to 43.5 ms depending on VOICE, so each
  correction is already in place when its note starts. Use it on a recorded take, for mixing and
  bouncing.

Both report their latency to the host, which plays the track that much earlier, so it stays in
time with the others. Changing it changes that latency, so it isn't automatable: set it and leave it.

### The display

The display shows the last four seconds, the newest at the right: the blue line is the voice as
sung, the bright line as corrected, the glow between them the correction, and the bars behind them
the notes it was pulled to. A rail lies on each note of the scale, the key's brighter. At the
lines' head a chip names the note and how far the voice is off it, `G1 +7 ct`.

The values along its top and bottom edges are its controls: drag one up or down, use the wheel
over it, or double-click it to reset; Shift is finer. VOICE has three choices: click it for its
list.

- **STRENGTH** below 100 % pulls only part of the way, for a voice that is helped rather than
  fixed.
- **DETUNE** moves the result off the note: a copy of the vocal at +8 ct under the original
  thickens it.
- **FORMANT** and **HOLD** shape the voice's colour. A big correction can thin a voice or make it
  chipmunky, because the formants move with the pitch; HOLD keeps them where they were. FORMANT
  moves them on purpose. At 0 and 0 % (the defaults) the formant filter is off.
- **A4** is the tuning reference.
- **VOICE** says where to look for the voice. Normal fits most singers; take Low for a bass voice
  that the plugin misses, and High for a high soprano or a whistle.

### The jellyfish

The jellyfish listens too. Its bell pulses and lights with the level, and its tentacles hang calm
while the voice is on its note (within 5 cents) and stir more the further it is off, all the way
from 50 cents. Switched off, it rests.

## Good to know

- **Latency:** REALTIME 0.25 ms, Quality 16 to 43.5 ms by VOICE. The host is told, and lines the
  track up.
- **Automation:** every parameter but REALTIME and VOICE can be automated; those two change the
  latency, so they aren't offered.
- **Saved with the project:** every setting and the zoom.
- **CPU:** 0.13 % of a core at the defaults.
- **One voice:** chords, a choir on one track or a mix go wrong. Correct each voice on its own
  track.
- **Zoom:** the project remembers it, and a new window opens at the zoom you last chose in any
  JellyComet plugin.
- **Hosts:** the CLAP passes `clap-validator`.
- **Display:** X11, or XWayland on a Wayland desktop, with a Vulkan driver.

## Troubleshooting

- **No correction, the display stays empty:** check that the power switch is on and that the
  voice is in VOICE's range; a low voice may need Low.
- **Notes jump to the wrong note:** the key or scale is wrong for the song. Chromatic corrects to
  the nearest note whatever the key.
- **The voice sounds thin or chipmunky after a big correction:** turn HOLD up.
- **The track sounds late against the others:** the host has to compensate the plugin's latency;
  check that its latency compensation is on.
- **The window stays black:** the editor needs a Vulkan driver (`vulkaninfo` should list your
  GPU).
