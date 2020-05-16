# Teensy-Audio-Piezo-Input
Piezo transducer input for Teensy Audio Shield

Status: I just began building this document... bear with me!

This project modifies a Teensy Audio Shield to accept the relatively weak singal from
a piezoelectric transducer. "Piezo" pickups are frequenly used to amplify acoustic
instruments such as the double bass, but could have other uses in vibration sensing
or wearable tech.

A typical requirement for a piezo is fairly high input impedance -- 1 or even
10 MegOhms, and of course low noise is desirable. These transducers are modeled
as a voltage source in series with a capacitance, and a resistive load can alter
the frequency response.

The Teensy Audio Shield uses a SGTL5000 audio codec, whose microphone input has
an input impedance of 2k Ohms. Some kind of buffering is needed. The first thing
that comes to mind is an op amp, but it actually needs a lot of support components
to operate on a single power supply.

Instead, a JFET does everything, albeit a bit more crudely. Here's my circuit.
I modified the Audio Shield, removing the microphone bias resistor. This lets me
use MICBIAS as a clean low-voltage power supply. I use it to power a basic JFET source
follower circuit. The input impedance is set by a resistor -- choose what you want.
I added a blocking capacitor, even though a piezo is naturally zero-biased, because
it can produce very low frequency signals when handled or bent, and some other
input sources might not be so friendly.

My choice of JFET... arrgh. JFETs are gradually dwindling in availability. Many
of the nicest types have gone obsolete. I need a JFET with a low gate-source
voltage, because I've only got about 3 V to play with. This is a bit of an
empirical exercise -- I've tested a lot of JFETs. The Philips BF861B is still
available in a surface mount package from Mouser. I also tried a through-hole
version of the 2N4393, and a surface mount version MMBF4394 might work. I would
always prepare to measure the DC source voltage on any JFET circuit, and prepare
to try a few pieces before you're happy.

I used a tiny surface mount breakout board, Mouser part # 485-1230, made by
Adafruit. Surface mount resistors would of course be cool to use, but I had to
use whatever I had.
