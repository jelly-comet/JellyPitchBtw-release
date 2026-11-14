# JellyPitchBtw

**Pitch correction for one voice, steered by a jellyfish.** One puck sets how fast a note is
pulled in and how far off its note a voice may be and be left alone, and a display shows the voice
as sung and as corrected. CLAP for Linux.

![JellyPitchBtw correcting a sung phrase: the jellyfish pad at the left, the voice as sung and as corrected in the display at the right](images/screenshot.png)

**[JellyPitchBtw on jelly-comet.github.io](https://jelly-comet.github.io/plugins/jellypitchbtw/)**: more screenshots, the manual to read or as a PDF, and every release.

Pick the key and scale, and every note is drawn to the nearest one in it. Drag the puck left for a
hard, robotic snap and right for a slow, natural glide; up humanizes, leaving notes that are
already close to their note alone, down corrects every one. The note follows the pitch as it is
sung, so a wide vibrato swings to the next note and back: the classic hard-tuned sound. It works
in real time: the host compensates the 0.25 ms of latency it reports, and while a voice is being
tuned the sound runs further behind, 3.8 ms on average. It is not a harmoniser and not a vocoder:
it corrects one voice at a time.

**[Read the manual](manual.md)** for every control and how to use it.

## What it's for

- **A hard-tuned lead vocal:** SPEED at 0 ms snaps every note to the key and scale at once, the robotic vocal tuning effect.
- **Gentle pitch correction:** a slower SPEED and some HUMANIZE pull in the notes that are clearly off and leave the rest of the take as it was sung.
- **Singing through it:** it tunes in real time, so it can stay on the track while you record and listen.
- **Backing vocals and solo lines:** any single voice, or an instrument that plays one note at a time.

## Features

- **13 scales in every key:** Chromatic, Major, Natural, Harmonic and Melodic Minor, Dorian, Phrygian, Lydian, Mixolydian, Locrian, Major and Minor Pentatonic and Blues.
- **One puck for the feel:** SPEED from 0 to 200 ms along the pad, HUMANIZE from 0 to 100 % (up to 50 cents) up it. 0 ms snaps at once.
- **The note follows the pitch:** a wide vibrato swings to its neighbour and back, for the hard-tuned sound.
- **0.25 ms of latency** in every voice range, reported to the host so the track stays in time. While a voice is being tuned the sound runs a little further behind, 3.8 ms on average.
- **The voice range beside the scale:** Low, Normal or High, each with its range in Hz.
- **A display that shows what it does:** the last four seconds, the voice as sung and as corrected, with STRENGTH, DETUNE and A4 set right in it.
- **A jellyfish that listens:** its bell pulses with your level and its tentacles stir the further you are off the note, calm within 5 cents.
- **Light:** 0.13 % of a CPU core at the defaults.
- **Zoom** from 100 to 200 %.
- **No network access and no telemetry.**

## Install

Download the latest version from the [Releases page](https://github.com/jelly-comet/JellyPitchBtw-release/releases),
or with these commands:

```bash
curl -LO https://github.com/jelly-comet/JellyPitchBtw-release/releases/download/v1.3.0/JellyPitchBtw-1.3.0-linux-x86_64.tar.gz
curl -LO https://github.com/jelly-comet/JellyPitchBtw-release/releases/download/v1.3.0/JellyPitchBtw-1.3.0-linux-x86_64.tar.gz.sha256
sha256sum -c JellyPitchBtw-1.3.0-linux-x86_64.tar.gz.sha256 && tar xzf JellyPitchBtw-1.3.0-linux-x86_64.tar.gz
cd JellyPitchBtw-1.3.0-linux-x86_64
```

Install for your user:

```bash
mkdir -p ~/.clap
rm -f ~/.clap/JellyPitchBtw.clap && cp JellyPitchBtw.clap ~/.clap/
```

Or for all users:

```bash
sudo mkdir -p /usr/lib/clap
sudo rm -f /usr/lib/clap/JellyPitchBtw.clap && sudo cp JellyPitchBtw.clap /usr/lib/clap/
```

Removing the old copy first avoids overwriting a file a running host has loaded. Then rescan plugins
in your DAW.

To uninstall:

```bash
rm -f ~/.clap/JellyPitchBtw.clap
```

## Requirements

- Linux x86-64 on a CPU with AVX2 (Intel Core from 2013, AMD from 2015), with glibc 2.31 or newer (Ubuntu 20.04, Debian 11, Fedora 32 and newer)
- A CLAP host. Tried in Bitwig Studio and REAPER.
- X11 or XWayland, and a Vulkan driver for the editor

Releases contain the CLAP plugin only.

## License

MIT, see [LICENSE](LICENSE). The licenses of the third-party code in the binaries are in
`THIRD-PARTY-LICENSES.txt` in each release archive.

CLAP is an open standard by the free-audio project. JellyPitchBtw is an independent project, not
affiliated with or endorsed by the makers of any other pitch correction.
