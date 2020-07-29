A write up on what is needed to build a passive towed hydrophone array that can do:
Track and isolate sound sources with elevation ( +90 to -90 degrees) and azimuth ( +180 to -180 degrees). 

Hardware:
It will need multiple passive piezoelectric sensors.
Some information on piezoelectric elements:
The problem with piezoelectric elements is that they are not well matched to typical audio inputs. The reason why these devices often sound "tinny" is because the piezo sensor presents its signal through a series capacitance which is small, typically 15nF or less. When wired to a normal 50 kilohm line input this forms a 200Hz high-pass filter, which eliminates the bass.  Because the piezo element has a very high impedance (1 MΩ typical), it should be buffered to avoid possible impedance mismatch with an existing audio system. 

The best piezoelectric sensors for listening is based on Aluminum Nitride and molybdenum. PZT-5 also known as SensorTech BM500,Channel 5500,Morgan PZT5A1 is widely used and possibly easier to find.

A document on how to build a basic, single element towed hydrophone: https://swfsc.noaa.gov/uploadedFiles/Divisions/PRD/Programs/Coastal_Marine_Mammal/Barlow%20et%20al%202008%20HydrophoneConstruction_TM-417.pdf
It's sensitivity is around -150 to -160 dB-V//microPa. 
The problem is that the opamp used in the mentioned document is not suitable for the voltage a USB connector delivers.

A suitable opamp for single +5Volt is a LME49724.

Compined preamplifier and buffer circuit, one per crystal:
The problem with piezoelectric and contact mics is that they are not well matched to typical audio inputs. 
The reason why these devices often sound tinny is because the piezo sensor presents its signal through a series capacitance which is small, typically 15nF or less. When wired to a normal 50 kilohm line input this forms a 200Hz high-pass filter, which eliminates the bass. 
Because the piezo disc has a very high impedance (1 MΩ typical), it should be buffered to avoid possible impedance mismatch with an existing audio system. This circuit acts as a impedance buffer, and some amplification does not hurt as long as it is around 40dB. 

The best piezoelectric sensors for listening is based on Aluminum Nitride and molybdenum. PZT-5 also known as SensorTech BM500,Channel 5500,Morgan PZT5A1 is widely used and more easily obtained. 



Also, the hydrophone will need to be modified so it doesn't rotate, or a MPU-6050 added per array to detect X and Y axis values. A GY-521 breakout board could be useful in those regards or a MPU-9150 Accelerometer + Gyro + Magnetometer (compass).
Passive towed hydrophone arrays in submarines monitors the bend and sag automatically.

If multiple sensor pods is used, those sensors could be useful as the position of the pods will change in respect to each other and the speed the array is towed at. 

Multiple sensor pods will enable: 
The possible to implement distance calculation  in the software if hydrophone pods with enough distance between them are used and sensors as described below is fitted (including the X,and Y axis.
Approximate values for fresh water and seawater, respectively, at atmospheric pressure are 1450 around 1500 m/s.

The speed of sound in water increases with increasing pressure, temperature and salinity.
If sensors that measures pressure, temperature and salinity is used to calculate the speed of sound in the water surrounding the hydrophones and  maximum rate of sampling is used, (192kHz, that is 192,000 times per second). 

I think it should be possible to calculate the distance to sound sources based upon those factors, and the known distance between two pods.

That should be interesting to those who monitors marine mammals.
I don't know if a AGC circuit is a good idea to implement,to avoid overloading the circuit.
Automatic gain control (AGC), is a closed-loop feedback regulating circuit in an amplifier or chain of amplifiers, the purpose of which is to maintain a suitable signal amplitude at its output, despite variation of the signal amplitude at the input. The average or peak output signal level is used to dynamically adjust the gain of the amplifiers, enabling the circuit to work satisfactorily with a greater range of input signal levels.


If those are a suitable distance and 45° degrees apart from each other in a flat circular array with 8  piezoelectric sensors, and hooked up to signal inputs with synchronised sampling for each piezoelectric element it should be possible to run a software called ManyEars or ODAS.
https://github.com/introlab/manyears
https://github.com/introlab/odas
Software demonstration:
https://youtu.be/n7y2rLAnd5I

About the software:
That software is used in robotics to to perform sound source localization, tracking, separation and post-filtering. It can do elevation ( +90 to -90 degrees) and azimuth ( +180 to -180 degrees). 

It cannot do distance calculations yet, but it should be possible to implement that in the software if hydrophone pods with enough distance between them are used and sensors as described below is fitted. Input from a couple of MPU-6050's or similar is also not implemented in the software.
Approximate values for fresh water and seawater, respectively, at atmospheric pressure are 1450 around 1500 m/s.
The speed of sound in water increases with increasing pressure, temperature and salinity.
If sensors that measures pressure, temperature and salinity is used to calculate the speed of sound in the water surrounding the hydrophones and  maximum rate of sampling is used, (192kHz, that is 192,000 times per second). I think it should be possible to calculate the distance to sound sources based upon those factors.

The open source hardware is called 8SoundsUSB or 16SoundsUSB.
https://sourceforge.net/projects/eightsoundsusb/
https://github.com/introlab/16SoundsUSB


The reqired preamp/buffer circut is located here:
https://github.com/Supermagnum/xSoundsMicrophones/tree/master/Hardware/Microphone-piezo




