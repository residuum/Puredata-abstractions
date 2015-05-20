# Abstractions for Puredata

This is a collection of abstractions that I have made for Puredata. I use
the Pd convention for adding a trailing tilde (~) to all objects, that
output or process audio. A lot of objects have accompaning help patches.

## Glue objects (glue)
`[bangonce]`: outputs only one bang, if the inlet receives a series of
1s. Useful for filtering MIDI data or data coming a comport object like
an arduino.

`[between]`: outputs a random float between two pre-defined values

`[bpmtoms]`: converts beats per minute to milliseconds for each beat,
inverse of `[mstobpm]`.

`[integral]`: integrates float values.

`[mstobpm]`: converts milliseconds for a beat to beats per minute, inverse
of `[bpmtoms]`.

`[mstofreq]`: converts milliseconds to a frequency.

`[note-vel-filter]`: filters a stream of MIDI data to only capture MIDI on,
off and velocity.

`[rec_play_switch]`: two switches for starting recording and playing loops
for `[note-vel-looper]` and `[sample-looper~]`.

`[s2f]`: converts symbol atoms to float atoms.

`[symbollen]`: gets the length of a symbol atom.

`[shift-router]`: routes input to one of six outlets with another input
for switching the outlets, useful for usage with push-buttons on an
arduino etc.

`[switch-bang]`: outputs bang alternatively on two outlets when receiving
a bang.

`[switch-matrix-6x6]`: routes 6 inlets to 6 outlets. Rows correspond to
outlets, columns to inlets, so the toggle in row 1 column 2 routes the
input from inlet 2 to outlet 1, e.g. useful for toggling synchronization
of `[sample-looper~]` instances.

`[switch-spigot]`: outputs 1 and 0 alternatively on the two outlets, useful
for switching two spigot objects.

`[timer-to-freq]`: measures the time between a bang on the left side and
the right side and converts the timespan to frequency.

`[trigger-filter]`: filters a stream of 0s and 1s and only outputs a value
when a change is occuring.

`[unwrap]`: wraps around values at specified lower and upper bound, e.g.
useful for rotation data.

## Effects and Mixing (fx)
`[bitcrusher~]`: simple bitcrusher effect.

`[distortion~]`: simple distortion effect.

`[normalize~]`: normalizes the sound and removes offset.

`[pan~]`: equal volume pan for mono.

`[phaser~]`: simple phaser effect, not to be confused with the built-in
sawtooth oscillator (`[phasor~]`)

`[pitchshift~]`, `[pitchshift2~]`: simple pitchshifter, each with its own
residual effects.

`[waveshaper~]`: simple waveshaper effect.


## Sound synthesis (synth)
`[303-saw~]`: a sawtooth oscillator and envelope following low pass filter
for acid sounds, but unfortunately not really similar to 303.

`[hoover~]`, `[hoover2~]`, `[hoover3~]`, `[hoover-phasor~]`: simple bass synth objects
for Dubstep basslines.

`[pulsewidth~]`: pulse oscillator with pulsewidth modulation.

`[squarewave~]`: squarewave oscillator.

`[triangle~]`: Triangle wave oscillator.


## Looper objects (loopers)
`[note-vel-looper]`, `[note-vel-looper-box]`: records and plays back MIDI loops
with adjustable start and stop, can be synchronized with other instances
of itself and `[sample-looper~]` instances.

`[sample-looper~]`, `[sample-looper-box~]`: records and plays back audio loops
with adjustable start, stop, playback speed and pitch, can be synchronized with
other instances of itself and `[note-vel-looper]` instances.

`[live-sampler~]`: records a sample and play it back as loops with MIDI notes.
Pitch of recorded loop is set to note 60, contains ADSR envelope, modulation
of playback pitch.

`[breakbeat~]`: loads a stereo sample of 8 beats length, slices it and plays it back as a breakbeat with adjustable playback speed and pitch. 
