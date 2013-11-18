A first attempt at network sound.

## Installation

Must run in ruby 2.0. 

    rvm install ruby-2.0

Clone repository, cd into project and

    bundle

on OSX, install [FluidSynth](http://sourceforge.net/apps/trac/fluidsynth/) via homebrew:

    brew install fluidsynth

Then run it from the project directory using the script:

    ./synth         

This should start fluidsynth with the soundfonts loaded.

The [Midikeys](http://www.manyetas.com/creed/midikeys) utility is handy for testing that things are working, you should see fluidsynth as an output and hear audio when playing.

Make sure you IAC driver is online (in the Audio Midi Setup application):

![](http://somebox.com/docs/iac.jpg)

Install [Midi Patchbay](http://notahat.com/midi_patchbay/). Then set up a patch that connects the OSX IAC driver to FludSynth:

![](http://somebox.com/docs/patchbay.jpg)

Now, try to make some noise:

    sudo tcpdump -i en0 -e -q -U | ./netaudio

## TODO

- deal with slowness of ruby and stdin. threading is not as nice as I had hoped.
- handle tcpdump messages better (more kinds, identify ssh etc)
- consider another way to get traffic other than tcpdump
- investigate new soundfonts, or make a custom one
- include some kind of visualization while things are working
- consider moving this to golang
