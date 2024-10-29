# VLC VideoLAN media player

## Home page

https://www.videolan.org/vlc/

Source code:

* https://code.videolan.org/videolan/vlc
* https://github.com/videolan/vlc

2023-11-01:

https://get.videolan.org/vlc/3.0.20/win64/vlc-3.0.20-win64.exe

## How MIDI to MP3

### Get a sound font

Download from one of the following:

* https://www.schristiancollins.com/generaluser.php: need to download zip then choose the sf2 file.
* https://github.com/FluidSynth/fluidsynth/blob/master/sf2/VintageDreamsWaves-v2.sf2: bad quality.

### Config VLC to use the sound font

`Tool`: `Preference`: `Input/Codecs`: `All` (bottom left): search MIDI: `FluidSynth`: `Browser`: choose above SF2 file.

After that, you can play MIDI files with VLC.

### Convert MIDI to MP3 with VLC

`Media`:
`Convert/Save`:
`Add`: choose MIDI need to convert:
`Convert/Save`: the Convert window appears.

Create a new `Profile`: click 🔧:
`Encapsulation` tab `MP3`:
`Audio codec` tab: choose Codec `MP3`, Bitrate 256 kb/s, Channels 2, Sample rate 48000 Hz:
`Save` the newly created profile:
On `Profile` line, click dropdown ▼, choose the newly created profile.


Destination file: choose output file name, e.g. `aoe_music2.mp3`:
`Start`.

Done.
