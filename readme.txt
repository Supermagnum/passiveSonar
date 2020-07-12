A write up on what is needed to build a passive towed hydrophone array that can do:
Track sound sources with elevation ( +90 to -90 degrees) and azimuth ( +180 to -180 degrees). 

Hardware:
It will need multiple passive piezoelectric sensors.
Some information on piezoelectric elements:
The problem with piezoelectric elements is that they are not well matched to typical audio inputs. The reason why these devices often sound "tinny" is because the piezo sensor presents its signal through a series capacitance which is small, typically 15nF or less. When wired to a normal 50 kilohm line input this forms a 200Hz high-pass filter, which eliminates the bass.  Because the piezo element has a very high impedance (1 MΩ typical), it should be buffered to avoid possible impedance mismatch with an existing audio system. 

The best piezoelectric sensors for listening is based on Aluminum Nitride and molybdenum. PZT-5 also known as SensorTech BM500,Channel 5500,Morgan PZT5A1 is widely used and possibly easier to find.

A document on how to build a basic, single element towed hydrophone: https://swfsc.noaa.gov/uploadedFiles/Divisions/PRD/Programs/Coastal_Marine_Mammal/Barlow%20et%20al%202008%20HydrophoneConstruction_TM-417.pdf
It's sensitivity is around -150 to -160 dB-V//microPa. 
The problem is that the opamp used in the mentioned document is not suitable for the voltage a USB connector delivers.
Also, the hydrophone will need to be modified so it doesn't rotate. A suitable long enough fin with a weight on the end could be the best solution.

Compined preamplifier and buffer circuit, one per crystal:
The preamplifier circuit mentioned below can be modified with a opamp to serve as a impedance buffer. Suitable opamps for single +5Volt is: OPA365,OPA1671,AD8613,TS922
 - low noise, good BW is important. 
A preamplifier for a microphone, it will need a buffer circuit powered by VCC, the bias circuit ( R1,C2, R5 on the preamp circuit )will need to be deleted as it is for electret microphone. The piezoelectric elements negative side needs to be directly grounded.The opamps output connects to +IN. Schematic:
https://sourceforge.net/projects/eightsoundsusb/files/Schematics/8SoundsUSB-MIC_REV2.0.pdf/download
Wires and cables should be shielded to minimize unwanted noise.
I don't know if a AGC circuit is a good idea to implement,to avoid overloading the circuit.
Automatic gain control (AGC), is a closed-loop feedback regulating circuit in an amplifier or chain of amplifiers, the purpose of which is to maintain a suitable signal amplitude at its output, despite variation of the signal amplitude at the input. The average or peak output signal level is used to dynamically adjust the gain of the amplifiers, enabling the circuit to work satisfactorily with a greater range of input signal levels.

If those are a suitable distance and 45° degrees apart from each other in a flat circular array with 8  piezoelectric sensors, and hooked up to signal inputs with synchronised sampling for each piezoelectric element it should be possible to run a software called ManyEars or ODAS.
https://github.com/introlab/manyears
https://github.com/introlab/odas

About the software:
That software is used in robotics to to perform sound source localization, tracking, separation and post-filtering. It can do elevation ( +90 to -90 degrees) and azimuth ( +180 to -180 degrees). 

It cannot do distance calculations, but it should be possible to implement that in the software if hydrophone pods with enough distance between them are used and sensors as described below is fitted.
Approximate values for fresh water and seawater, respectively, at atmospheric pressure are 1450 around 1500 m/s.
 The speed of sound in water increases with increasing pressure, temperature and salinity.
If sensors that measures pressure, temperature and salinity is used to calculate the speed of sound in the water surrounding the hydrophones and  maximum rate of sampling is used, (192kHz, that is 192,000 times per second). I think it should be possible to calculate the distance to sound sources based upon those factors.

The open source hardware is called 8SoundsUSB or 16SoundsUSB.
https://sourceforge.net/projects/eightsoundsusb/
https://github.com/introlab/16SoundsUSB





