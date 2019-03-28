# **Digital Communications Project**
Simulating the performance of different modulation schemes, such as, [**BPSK**](#binary-phase-shift-keying-modulation-bpsk), [**QPSK**](#quadrature-phase-shift-keying-modulation-qpsk), [**FSK**](#frequency-shift-keying-fsk), [**QAM**](#quadrature-amplitude-modulation-qam) in an Additive White Gaussian Noise, AWGN environment.

## Simulation Environment Settings
- The simulation is done using 2 different parameter sets for the Random Input Generator defined below.
    * **Set 0**: Sample Time = 0.1 s, Samples Per Frame = 100
    * **Set 1**: Sample Time = 1 s, Samples Per Frame = 100
- The noise level is set to 10 dB.
- The simulation period is set to 100. 
- Integer Random Generator seed is set to Auto.
- Noise initial random seed is set to 67.
- All scatter plots are produced at a noise level (Eb/No) of 10 dB.
- All BER diagrams use a noise level of [-10, 10] dB.
- The simulation period is set to 100.

## Reproducing Scatter Plots
To reproduce the scatter plots, kindly do the following: 
- Set the simulation parameters as mentioned in the [**Simulation Environment Settings**](#simulation-environment-settings), it will most likely be already set, except for the Random Input Generator parameter sets.
- Double click the AWGN channel, and set the noise level (Eb/No) to 10 dB.
- Set the simulation time to 100 and click run. 

## Reproducing BER Diagrams
To reproduce the BER diagrams, kindly do the following:
- Set the simulation parameters as mentioned in the [**Simulation Environment Settings**](#simulation-environment-settings), it will most likely be already set, except for the Random Input Generator parameter sets. 
- Double click the AWGN channel, and set the noise level (Eb/No) to variable called ```EbNo```.
- From Matlab's command line, run the BER diagram tool using the command ```bertool```.
- From the ```Theoretical``` tab in the BER tool window, set the following:
   * Eb/No range to -10:10.
   * Channel type to AWGN.
   * The respective Modulation type and order. 
- Click ```Run``` to plot the theoretical exact BER diagram.
- From the ```Monte Carlo``` tab in the BER diagram tool, set the following:
   * Eb/No range to -10:10.
   * Simulink model to the path of the respective file for each modulation scheme.
   * Set the BER vairable name to ```BER```.
   * Set the simulation limits as desired. Left as default (Number of erros = 100, number of bits = 1e8).
- Click ```Run``` to plot the Monte Carlo BER diagram.

## **Binary Phase-Shift Keying Modulation (BPSK)**
### - Definition 
BPSK is a two phase modulation scheme, where the 0’s and 1’s in a binary message are represented by two different phase states in the carrier signal: theta = 0 for binary 1 and theta = 180 for binary 0.

### - Schematic
```
- Random Generator set size = 2
- Phase offset (rad) = 0
```

![High level view of the modulation/demodulation scheme](/figures/schematics/BPSK.PNG)


### - Transmitter Scatter Plots
* Parameter Set 0:

    ![Parameters set 0](/figures/scatter_plots/before/BPSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](/figures/scatter_plots/before/BPSK2.PNG) 
### - Receiver Scatter Plots
* Parameter Set 0: 

    ![Parameters set 0](/figures/scatter_plots/after/BPSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](/figures/scatter_plots/after/BPSK2.PNG) 
### - BER Diagram
* Simulation 0 (green) is using parameter set 0.
* Simulation 1 (red) is using parameter set 1.

    ![BER Diagram](/figures/ber_diagrams/BPSK.PNG)

___
## **Quadrature Phase-Shift Keying Modulation (QPSK)**
### - Definition 
QPSK is a form of Phase Shift Keying in which two bits are modulated at once, selecting one of four possible carrier phase shifts (0, 90, 180, 270). QPSK allows the signal to carry twice as much information as ordinary PSK using the same bandwidth.
### - Schematic
```
- Random Generator set size = 4
- Phase offset (rad) = pi/4
``` 
![High level view of the modulation/demodulation scheme](/figures/schematics/QPSK.PNG) 
### - Transmitter Scatter Plots
* Parameter Set 0:

    ![Parameters set 0](/figures/scatter_plots/before/QPSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](figures/scatter_plots/before/QPSK2.PNG) 
### - Receiver Scatter Plots
* Parameter Set 0: 

    ![Parameters set 0](/figures/scatter_plots/after/QPSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](/figures/scatter_plots/after/QPSK2.PNG) 
### - BER Diagram
* Simulation 0 (green) is using parameter set 0.
* Simulation 1 (red) is using parameter set 1.

    ![BER Diagram](/figures/ber_diagrams/QPSK.PNG)

___
## **Frequency Shift Keying (FSK)**
### - Definition 
FSK is the frequency modulation system in which digital information is transmitted through the discrete frequency change of a carrier wave. The simplest FSK is binary FSK (BFSK).
### - Schematic
```
- Random Generator set size = 2
- M-ary number = 2
- Frequency separation = 6 Hz
- Samples per symbol = 17
``` 
![High level view of the modulation/demodulation scheme](/figures/schematics/FSK.PNG) 
### - Transmitter Scatter Plots
* Parameter Set 0:

    ![Parameters set 0](/figures/scatter_plots/before/FSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](/figures/scatter_plots/before/FSK2.PNG) 
### - Receiver Scatter Plots
* Parameter Set 0: 

    ![Parameters set 0](/figures/scatter_plots/after/FSK1.PNG) 
* Parameter Set 1:

    ![Parameters set 1](/figures/scatter_plots/after/FSK2.PNG) 
### - BER Diagram
* Simulation 0 (green) is using parameter set 0.
* Simulation 1 (red) is using parameter set 1.

    ![BER Diagram](/figures/ber_diagrams/FSK.PNG)

___
## **Quadrature Amplitude Modulation (QAM)**
### - Definition
QAM is a signal in which two carriers shifted in phase by 90 degrees (i.e. sin and cos) are modulated and combined. As a result of their 90 phase difference they are in quadrature and this gives rise to the name. Often one signal is called the In-phase or I signal, and the other is the quadrature or Q signal. 
### - Types
* QAM 16
* QAM 64
### - Schematic
```
- Random Generator set size = 16, 64
- M-ary number = 16, 64
- Normalization method = Average Power
- Phase offset (rad) = 0
- Average power referenced to 1 Ohm = 1 Watts
``` 
* **QAM 16**

    ![High level view of the modulation/demodulation scheme](/figures/schematics/16QAM.PNG)

* **QAM 64**

    ![High level view of the modulation/demodulation scheme](/figures/schematics/64QAM.PNG) 
### - Transmitter Scatter Plots
* **QAM 16**:
    * Parameter Set 0

        ![Parameters set 0](/figures/scatter_plots/before/16QAM1.PNG)
    * Parameter Set 1

        ![Parameters set 1](/figures/scatter_plots/before/16QAM2.PNG)
* **QAM 64**
    * Parameter Set 0

        ![Parameters set 0](/figures/scatter_plots/before/64QAM1.PNG)
    * Parameter Set 1

        ![Parameters set 1](/figures/scatter_plots/before/64QAM2.PNG)
### - Receiver Scatter Plots
* **QAM 16**:
    * Parameter Set 0

        ![Parameters set 0](/figures/scatter_plots/after/16QAM1.PNG)
    * Parameter Set 1

        ![Parameters set 1](/figures/scatter_plots/after/16QAM2.PNG)
* **QAM 64**
    * Parameter Set 0

        ![Parameters set 0](/figures/scatter_plots/after/64QAM1.PNG)
    * Parameter Set 1

        ![Parameters set 1](/figures/scatter_plots/after/64QAM2.PNG)
### - BER Diagram
* Simulation 0 (green) is using parameter set 0.
* Simulation 1 (red) is using parameter set 1.

    * **QAM 16**

        ![BER Diagram](/figures/ber_diagrams/16QAM.PNG)
    * **QAM 64**

        ![BER Diagram](/figures/ber_diagrams/64QAM.PNG)
