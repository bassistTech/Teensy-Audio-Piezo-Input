# Teensy-Audio-Piezo-Input
Piezo transducer input for Teensy Audio Shield

Status: I just began building this document... bear with me!

This project modifies a Teensy Audio Shield to accept the relatively weak singal from
a piezoelectric transducer. "Piezo" pickups are frequenly used to amplify acoustic
instruments such as the double bass, but could have other uses in vibration sensing
or wearable tech.

A typical requirement for a piezo is fairly high input impedance -- 1 or even
10 M$\Omega$, and of course low noise is desirable. These transducers are modeled
as a voltage source in series with a capacitance, and a resistive load can alter
the frequency response.
