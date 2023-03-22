# EM-TDR-Testing

| Task Name | Description | Progress |
| ------------- | ------------- | ------------- |
| [Numerical Scheme](#numerical-scheme-25-d-approach)  | Brief introduction of the 2.3-D numerical scheme  | Finished  |
| [Numerical simulation test](#numerical-simulation-test) | 2-D pipe cross-section in different scenarios: <ul><li>[Dis-bond coating with intact coating and metalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-intact-coating-no-corrosion)</li><li>[Dis-bond coating with intact/ broken coating and intact matalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-broken-coating-no-corrosion)</li></ul> | Finished  |
| [Numerical sensitivity test of corrosion](#numerical-sensitivity-test) | Numerical test of varies metalic loss due to corrosion as well as coating damages <ul><li>[2-D cross-sections](#numberical-simulation-result-of-the-2-d-cross-sections)</li><li>[Characteristic impedance changes](#characteristic-impedance-changes-in-different-scenarios)</li></ul> | Finished|
| [EM-TDR prototype development](#em-tdr-prototype-development) | EM waveform generating and receiving set up | Finished|
| [EM-TDR prototype evaluation](#em-tdr-prototype-evaluation) | Pipeline damage sensitivity lab test | Finished |



### Numerical Scheme: 2.5-D approach

In most of the case, the pipeline has relative thin pipe wall but very long length, making it is very expensive to simulate in full 3-D scenario. To compensate such dilema, we addopt the 2.5-D approach: First, we simulate the cross-section of every possiable pipe condition. As result, we can calculate the characteristic impednace per unit length of these conditions. The cross-section simulation is shown in the following figure as an example: 

| ![characteristic impednace calculation](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture1.png) |
|:--:|
| *Example of calculating the characteristic impednace of the unit length and simulation of the 2-D cross-section* |

Secondly, we assemble these sections in the longitudinal into a 1-D model and simulate the EM-TDR response. 

| ![2.5-D approach](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture2.png) |
|:--:|
| *Assemble the 2-D cross-sections into 1-D model in longitudinal direction* |

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

### EM-TDR prototype evaluation

The pipeline damage sensitivity lab test included the gap (0 – 3 cm) between two 6 ft stainless steel pipes. 
The laboratory set up for the pipe is shown in the figure: 
| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture13.png) |
|:--:|
| *Laboratory set up to emulate the damaged pipe* |

We also conducted numerical simulation of the laboratory set up. The results are shown: 

| ![EM-TDR equipment](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture14.png) |
|:--:|
| *Numerical simulation of the lab testing set up. The top row is the numerical model. The bottom row is the voltage potential field.* |
