# NIST WWV Signal Mapping

Collection of predicted and field tested signal strength measurements of NIST WWV Time and Frequency Station looking specifically at the 5MHz transmission.

## Overview

Assisting the Microwave Photonics Laboratory at Colorado School of Mines with determining whether their lab is in a deadzone from NIST's WWV Time and Frequency Station located north of Fort Collins, CO.

## Why we mapped the signal

WWV transmits from Fort Collins, Colorado. NIST operates the station. It
gives the time and a reference frequency on 2.5, 5, 10, 15, 20, and 25 MHz.

A receiver gets the signal in two ways. The ground wave follows the surface
of the earth. It becomes weak as the distance increases. The sky wave goes
up, reflects from the ionosphere, and comes back to earth at a longer
distance. Between the two, there is an area with a weak signal. The name is the skip
zone, or the dead zone. The ground wave is too weak there. The sky wave
passes over the area. Additionally, the ground wave can be disrupted by terrian features
that create a RF "shadow" where the signal is much weaker than another point at the same distance
without the terrain obstruction.

Golden, Colorado where Colorado School of Mines is located, lays between
Lookout Mountain to the west, and both north and south table mountain to the east.
The microwave photonics laboratory is conducting research focused on technology for 
receiving signals falling in the very low frequency to very high frequency range.

During their research the microwave photonics lab elected to use the NIST WWV 5MHz
Time and Frequency signal as a consistent reference point for their research. 
After several attempts to reference the signal, they were unable to receive it. 

They wanted to verify whether the signal was present or if their device was not actually
receiving the signal. I was brought in to help test whether the lack of signal was due to 
a RF "shadow". 

## How we predicted the dead zone

Utilizing Radio Mobile; a free RF propagation simulation and mapping software by Roger Coude (VE2DBE),
We determined that there was likely a shadow created from north table mountain.

![Settings for all Radio Mobile simulations](images/WWV Radio Mobile Antenna and Receiver settings.png)

The above photo is all of the settings that were used for all simulation using Radio Mobile.

![State Wide scale map with Radio Mobile signal simulation overlay](images/WWV Radio Mobile heatmap zoomed out.png)

This photo shows the Radio Mobile signal simulation overlay at the state wide scale.

![City of Golden scale map with Radio Mobile signal simulation overlay](images/WWV Radio Mobile heatmap zoomed in.png)

This photo shows the Radio Mobile signal simulation overlay at the city level scale. This simulation pointed toward the fact
that north table mountain creates a "RF" shadow or deadzone. 

Using the state wide heatmap, six test locations were selected. Radio Mobile simulation showed the likely areas for strongest signal, 
then Scada Core RF Path, a free online tool to determine line of sight between two antenna's was used to select points.

| Site Name | Position (Lat/Long) | Distance from WWV | Reason for selection |
|---|---|---|---|
|Frederick, CO|40.10452096063513, -104.94304029222081|64.34Km|Scada Core RF Path|
|Layfette, CO|39.9816698215178, -105.06295871223249|77.49Km|Scada Core RF Path|
|Arvada, CO|39.8267488739129, -105.08258567515914|94.76Km|Scada Core RF Path|
|Golden, CO CSM Intramural Field|39.74992271582115, -105.22568124018566|104.43Km|Scada Core RF Path|
|Golden, CO Lookout Mountain Mines M pullout|39.74620930581129, -105.23974371573536|105.03Km|Scada Core RF Path|

##Test methodology
Equipment used:
1.RTL SDR
1.SMA-F to BNC-M to BNC-F to PL-259-M adapters
1.PL-259-F 5M Cable (Radioddity)
1.Radioddity HF-009 portable HF antenna
1.Razer Blade 16"
1.Bodnar GPS-Disciplined 10MHz Source

Software used:
1.SDR#

SNR and Absolute delivered power measurements were taken via the RTL-SDR and SDR#, 
at that same time the data was demodulated to see if any of the voice announcements could be heard.
The Radioddity HF-009 provides access for the RTL-SDR to the 5MHz frequency.
Prior to initating testing on the 5MHz band the RTL-SDR was frequency calibrated using the 
Bodnar GPS-Disciplined 10MHz Source.

Once the antenna was set-up and connected to the SDR, SDR# was then set to 5MHz and 
IQ samples with gain settings of 20.70, bandwidth of 10kHz, AM Modulation, and sample rate of 2.4 MS/s.

