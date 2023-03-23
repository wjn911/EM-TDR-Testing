# EM-TDR-Testing

| Task Name | Description | Progress |
| ------------- | ------------- | ------------- |
| [Numerical Scheme](#numerical-scheme-25-d-approach)  | Brief introduction of the 2.3-D numerical scheme  | Finished  |
| [Numerical simulation test](#numerical-simulation-test) | 2-D pipe cross-section in different scenarios: <ul><li>[Dis-bond coating with intact coating and metalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-intact-coating-no-corrosion)</li><li>[Dis-bond coating with intact/ broken coating and intact matalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-broken-coating-no-corrosion)</li></ul> | Finished  |
| [Numerical sensitivity test of corrosion](#numerical-sensitivity-test) | Numerical test of varies metalic loss due to corrosion as well as coating damages: <ul><li>[2-D cross-sections](#numberical-simulation-result-of-the-2-d-cross-sections)</li><li>[Characteristic impedance changes](#characteristic-impedance-changes-in-different-scenarios)</li></ul> | Finished|
| [EM-TDR prototype development](#em-tdr-prototype-development) | EM waveform generating and receiving set up | Finished|
| [EM-TDR prototype evaluation](#em-tdr-prototype-evaluation) | Pipeline damage sensitivity lab test: <ul><li>[Experiment set up](#damaged-pipe-set-up)</li><li>[Laboratory testing results](#laboratory-testing-results)</li><li>[Numerical simulation](#numerical-simulation)</li><li>[Comarision between numerical simulation and laboratory testing](#comparision-between-numerical-simulation-and-laboratory-measurements)</li></ul> | Finished |
| [C-FER Deepwell blind simulator test](#c-fer-deepwell-simulator-test) | Blind test on three well with full of features: <ul><li>[Wellbore schematic diagram](#c-fer-deepwell-simulator-test)</li><li>[Feature identification scheme](#feature-identification)</li></ul> | Finished |


### Numerical Scheme: 2.5-D approach

In most of the case, the pipeline has relative thin pipe wall but very long length, making it is very expensive to simulate in full 3-D scenario. To compensate such dilema, we addopt the 2.5-D approach: First, we simulate the cross-section of every possiable pipe condition. As result, we can calculate the characteristic impednace per unit length of these conditions. The cross-section simulation is shown in the following figure as an example: 

| ![characteristic impednace calculation](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture1.png) |
|:--:|
| *Example of calculating the characteristic impednace of the unit length and simulation of the 2-D cross-section* |

Secondly, we assemble these sections in the longitudinal into a 1-D model and simulate the EM-TDR response. 

| ![2.5-D approach](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture2.png) |
|:--:|
| *Assemble the 2-D cross-sections into 1-D model in longitudinal direction* |

[Back to top](#em-tdr-testing)
### Numerical simulation test
#### Numerical simulation Scenario 1: Dis-bond coating, intact coating, no corrosion
In this case, the intruding fluid is mostly air. A little air-packet is form between coating layer and metalic pipe. We also demonstrate varies thickness of the intruding air layer.
The result is shown below: 

| ![Dis-bond pipe](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture3.png) |
|:--:|
| *Numerical simulation of the dis-bond coating filled with air. The cross-sections illustrate the voltage potential field as well as the electric field* |

#### Numerical simulation Scenario 1: Dis-bond coating, broken coating, no corrosion

Here we demonstrate a example of 2-D cross-section simulation of water intrusion scenario with both intact coating as well as broken coating: 
| ![Dis-bond pipe](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture4.png) |
|:--:|
| *Numerical simulation of the dis-bond coating filled with water. Here it is showing the coating is not broken, broken width of 10&deg;, and 20&deg;, respectively. The cross-sections illustrate the voltage potential field as well as the electric field* |

[Back to top](#em-tdr-testing)
### Numerical sensitivity test

In this numerical test, we add the metalic loss to the model. 
The water intrusion is under the coating, 30&deg; wide. The water layer is 10% casing thickness. 
Casing corrosion: 10&deg; wide, filled with water.
Casing corrosion lost: 10% of the casing thickness per step. In the following figure, we only show every 20% casing thichness due to the limited space.

| ![2-D numerical model](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture5.png) |
|:--:|
| *Numerical model of water intrusion under coating* |

#### Numberical simulation result of the 2-D cross-sections

The voltage potential field as well as the electric field compare with the baseline field (intact scenario) is shown: 
| ![2-D numerical simulation results](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture6.png) |
|:--:|
| *Numerical simulation results* |

#### Characteristic impedance changes in different scenarios

For EM-TDR be able to detect the reflected signal, we are more interested in the characteristic impedance changes when corrosion happens. Here we plot the characteristic impedance changes via different corrosion size as well coating damage size: 
- Intrusion angle: 10&deg; – 30&deg;, step: 10&deg;
- Intrusion thickness: 50% -- 200% of casing thickness, step: 50%
- Coating broken angle: 10&deg; -- 30&deg;, step: 10&deg;
- Casing corrosion angle : 10&deg; -- 30&deg;, step: 10&deg;
- Casing corrosion thickness: 20% -- 80% of the casing thickness, step: 20%

Here are the results plotted in figures: 

| ![2-D numerical simulation results](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture7.png) |
|:--:|
| *Corrosion on casing, coating broken angle: 0&deg;* |

| ![2-D numerical simulation results](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture8.png) |
|:--:|
| *Corrosion on casing, coating broken angle: 10&deg;* |

| ![2-D numerical simulation results](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture9.png) |
|:--:|
| *Corrosion on casing, coating broken angle: 20&deg;* |

| ![2-D numerical simulation results](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture10.png) |
|:--:|
| *Corrosion on casing, coating broken angle: 30&deg;* |

[Back to top](#em-tdr-testing)
### EM-TDR prototype development

The drawing of the EM-TDR set up is shown in the following schematic: 

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture12.png) |
|:--:|
| *EM-TDR prototype: schematic of the acquisitionset up* |

The detail parameters of the waveform generator and oscilloscope are listed in the following tables:

| Oscilloscope ||
| ------------- | ------------- |
| Number of output | 4 channels |
| Frequency range | 500 MHz to 8 GHz|
| Mechanical (W x H x D)<br>Weight | 16.9 x 12.9 x 9 inch (430 x 330 x 230 mm)<br> 26.4 lbs (12 kg)|
| Power source | 380 Watts | 
| Operating enviroment | Temperature: 5 &deg;C to 40 &deg;C <br> Humidity: < 80% RH <br> Altitude: 9,842 ft (3000 m)|

| Arbitrary waveform generator ||
| ------------- | ------------- |
| Number of output | 2 channels |
| Frequency range | 1 μHz to 2 GHz |
| Amplitude offset | -2.5 V to + 2.5 V | 
| Bandwidth | 2 GHz |
| Mechanical (W x H x D)<br>Weight | 17.7 x 6.3 x 13.4 inch (450 x 160 x 340 mm)<br> 4.4 lbs (9.7 kg)|
| Power source | 100 to 240 Vac <br>120 Watts (max) | 
| Operating enviroment | Temperature: 0 &deg;C to 50 &deg;C <br> Humidity: 8% to 90% RH <br> Altitude: 10,000 ft (3048 m)|

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture11.png) |
|:--:|
| *EM-TDR prototype. a: Oscilloscope; b: Arbitrary waveform generator* |

[Back to top](#em-tdr-testing)
### EM-TDR prototype evaluation

#### Damaged pipe set up
The pipeline damage sensitivity lab test included the gap (0 – 3 cm) between two 6 ft stainless steel pipes. 
The laboratory set up for the pipe is shown in the figure: 
| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture13.png) |
|:--:|
| *Laboratory set up to emulate the damaged pipe* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture15.png) |
|:--:|
| *Laboratory set up to emulate the 130&deg; and 15&deg; damage in the pipe* |

#### Laboratory testing results
The laboratory testing consist of three different damage width: 245&deg;, 130&deg;, and 15&deg;. Each damage width consist of 0 -- 30 mm damage length. We conducted each of these settings with 6 different frequencies: 
- 2 GHz sine waveform
- 1 Ghz sine waveform
- 770 MHz square waveform
- 500 MHz square waveform
- 300 MHz square waveform
- 150 MHz square waveform and Gaussian waveform
We also test on the intact pipeline as the baseline measurement, and exam the difference between damaged-pipe data and intact-pipe data.
Here are some of the measured results:

##### EM-TDR measurement of the 245&deg; damage in the pipe with different frequencies

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture16.png) |
|:--:|
| *Left: raw data. Right: data after processed* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture17.png) |
|:--:|
| *Left: raw data. Right: data after processed* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture18.png) |
|:--:|
| *Left: raw data. Right: data after processed* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture19.png) |
|:--:|
| *Left: raw data. Right: data after processed* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture20.png) |
|:--:|
| *Left: raw data. Right: data after processed* |

Based on these measurements, we can see:

- Reflections from gap very clear in the differential plot: both primary and multiple (green).
- End reflections and the first multiple of the gap separated clearly on the differential plot.
- Initial reflections and the gap reflections separated much clearer on the differential plot.
- Reflections from gap got clearer in the differential plot: both primary and multiple (green). 
- Amplitude of the reflections, except the initial reflection, got bigger as the gap increases, vice versa. 

##### EM-TDR measurement of the 130&deg; and 15&deg; damage in the pipe with different frequencies

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture21.png) |
|:--:|
| *EM-TDR measurement of 130&deg; damage in the pipe. Measured frequency: 770 MHz. Left: raw data. Right: data after processed* |

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture22.png) |
|:--:|
| *EM-TDR measurement of 15&deg; damage in the pipe. Measured frequency: 770 MHz. Left: raw data. Right: data after processed* |

#### Numerical simulation
We also conducted numerical simulation of the laboratory set up. The results are shown: 

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture14.png) |
|:--:|
| *Numerical simulation of the lab testing set up. The top row is the numerical model. The bottom row is the voltage potential field.* |

#### Comparision between numerical simulation and laboratory measurements
To evaluate the most realistic scenario, we used the smallest gap width (15&deg;) settting for comparision between numerical simulation and the laboratory testing. The results are shown in the following figure:
- This is differential plot: we subtract the intact casing signal from all the other scenarios.
- After subtraction, the intact signal is zeros (flat red line), the other differential signal is in blue curves.
- In the lab testing, each testing cannot be exactly the same, so after subtraction, we can see the visible entry reflections residuals.

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture23.png) |
|:--:|
| *Comparision between numerical simulation and laboratory testing. Left: numerical simulation. Right: laboratory testing* |

[Back to top](#em-tdr-testing)
### C-FER Deepwell simulator test

This is a blind test on the C-FER Deepwell simulator. 
- Well size (OD): 4.5 inch, 5.5 inch, and 7.0 inch;
- Well depth: 82 ft.

The schematic diagram and the photograph of the wellheads is shown: 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture24.png) |
|:--:|
| *Left: photograph of the three wellheads. Right: schematic diagram of the three welll.* |

#### Feature identification

Signal based identification:
- Raw identification of the reflective signals: **Looking for anomalies**;
- Using frequency-spatial resolution relationship: **Looking for consistency cross different frequencies**.

Inversion based identification:
- LSR (Least-Squared Root)-inversion with out considering attenuation
- LSR-inversion with attenuation compensation: because we can easily identify the primary multiple reflection, so we can roughly estimate the Q value based on the amplitude changes from entry-reflection to primary multiple.

For different size of features, special resolution is relatively **frequency dependent**:
- The feature size $(h)$ is bigger than $1/4$ of of max wavelengths $(\lambda = 1/f)$:can be resolved by all frequencies $\frac{\lambda_{max}}{4} \le h$.
- The feature size $(h)$ is not bigger than $1/4$ of of all wavelengths $(\lambda = 1/f)$:cannot be resolved by all frequencies $\frac{\lambda_{min}}{4} \le h \le \frac{\lambda_{max}}{4}$.

So, ultilizing the frequency dependence, we can identify the features by examing both the reflection waveforms. If the reflected waveforms are all most the same in different frequencies, the size of the feature is likely larger than the quater of largest wavelength we used.Here is an example from 7-inch wellbore testing:

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture25.png) |
|:--:|
| *Example of EM-TDR reflection from a feature that is larger than the quater of the longest wavelength used.* |

Contrary, if the reflected waveforms gradually merged togather as the freqeuncy decrease (wavelength increase), the size of the feature is likely between the quater of the smallest wavelength and the quater of the largest wavelength we used. Here is an example from the same 7-inch wellbore testing:

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture26.png) |
|:--:|
| *Example of EM-TDR reflection from a feature that is between the quater of the shortest wavelength and the quater of the longest wavelength used.* |

