# EM-TDR-Testing

| Task Name | Description | Progress |
| ------------- | ------------- | ------------- |
| [Numerical Scheme](#numerical-scheme-25-d-approach)  | Brief introduction of the 2.3-D numerical scheme  | Finished  |
| [Numerical simulation test](#numerical-simulation-test) | 2-D pipe cross-section in different scenarios: <ul><li>[Dis-bond coating with intact coating and metalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-intact-coating-no-corrosion)</li><li>[Dis-bond coating with intact/ broken coating and intact matalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-broken-coating-no-corrosion)</li></ul> | Finished  |
| [Numerical sensitivity test of corrosion](#numerical-sensitivity-test) | Numerical test of varies metalic loss due to corrosion as well as coating damages: <ul><li>[2-D cross-sections](#numberical-simulation-result-of-the-2-d-cross-sections)</li><li>[Characteristic impedance changes](#characteristic-impedance-changes-in-different-scenarios)</li></ul> | Finished|
| [EM-TDR prototype development](#em-tdr-prototype-development) | EM waveform generating and receiving set up | Finished|
| [EM-TDR prototype evaluation](#em-tdr-prototype-evaluation) | Pipeline damage sensitivity lab test: <ul><li>[Experiment set up](#damaged-pipe-set-up)</li><li>[Laboratory testing results](#laboratory-testing-results)</li><li>[Numerical simulation](#numerical-simulation)</li><li>[Comarision between numerical simulation and laboratory testing](#comparision-between-numerical-simulation-and-laboratory-measurements)</li></ul> | Finished |
| [C-FER Deepwell blind simulator test](#c-fer-deepwell-simulator-test) | Blind test on three well with full of features: <ul><li>[Wellbore schematic diagram](#c-fer-deepwell-simulator-test)</li><li>[Feature identification scheme](#feature-identification)</li><li>[Iterative workflow of inversion process](#iterative-workflow-of-inversion-process)</li><li>[Interpretation and inversion results](#interpretation-and-inversion-results)</li><li>[Integrity features on the casings](#integrity-features-on-the-casings)</li><li>[Ground truth matrix](#ground-truth-matrix)</li><li>[Comparision between EM-TDR interpretation results and ground truth](#comparision-between-em-tdr-interpretation-results-and-ground-truth)</li><li>[EM-TDR interpretation result evaluation](#em-tdr-interpretation-result-evaluation)</li></ul> | Finished |
| [Preliminary Field Test: MacDonald Island](#preliminary-field-test-macdonald-island) | <ul><li>[Wellbore test: Turner Cut W-1E surface casing](#wellbore-test-turner-cut-w-1e-surface-casing)</li><li>[Gathering Pipeline test](#gathering-pipeline-test)</li></ul> | Finished |
| Lab simulated pipeline leakage | Including: coading dis-bonded, water intrusion, and metal loss | In progress | 
| Controlled enviroment testing of the pipe burried in the soil | The soil surrounding the pipe could be modify to emulate the water leakage | Planned |
| Field blind test at the Johnson City facility | Blind testing of EM-TDR in the simulated field enviroment | Planned |
| Comparision between EM-TDR and UT (Ultrasonic testing ) | Comaring two different detecting technique on the pipeline | Planned |

### Numerical Scheme: 2.5-D approach

In most of the case, the pipeline has relative thin pipe wall but very long length, making it is very expensive to simulate in full 3-D scenario. To compensate such dilema, we addopt the 2.5-D approach. More detail about this approach can be seen at [Wang & Wu (2020)](https://doi.org/10.1016/j.ijggc.2020.103002): First, we simulate the cross-section of every possiable pipe condition. As result, we can calculate the characteristic impednace per unit length of these conditions. 

We ultilize the Poisson equation:
$$\nabla \cdot (\varepsilon_{r}\nabla{V}) = - \frac{\rho}{\varepsilon_{0}}$$
and the Gauss’s law:
$$q = \varepsilon_{0} \oint\limits_S{\varepsilon_{r}(x,y){E}(x,y)} \cdot d{n}$$
In addtion, we know that the capacitance C per unit length:
$$C = \frac{q}{V_{0}}$$
and characteristic impedance (per unit length):
$$Z = \sqrt{\frac{L}{C}}$$

Combining the above equations, we can calculated the characteristic impedance (per unit length) of the cross-section:

$$Z = \sqrt{\frac{L}{C}} = \sqrt{\frac{LC_{0}}{CC_{0}}} = \frac{1}{v_{0}\sqrt{CC_{0}}}$$

The cross-section simulation is shown in the following figure as an example: 
| ![characteristic impednace calculation](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture1_1.png) |
|:--:|
| *Example of calculating the characteristic impednace of the unit length and simulation of the 2-D cross-section. a: The dielectric permittivity model. b: Numerical simulated voltage potential field. c: Numerical simulated electric field.* |

Secondly, we can assemble each of the section, calculated from the above 2-D model, into 1-D model in the longitudinal direction to simulate the EM-TDR response:

$$R = \frac{V_r}{V_i} = \frac{Z_L - Z_0}{Z_L + Z_0}$$
 
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

[Back to top](#em-tdr-testing)
#### Iterative workflow of inversion process

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture27.png) |
|:--:|
| *Left: Workflow chart of the iterative workflow of inversion process. Right: forward modeling workflow used in the intersion.* |

#### Interpretation and inversion results

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture28.png) |
|:--:|
| *Intersion and interpretation results of all three wells* |

#### Integrity features on the casings

The features were revealed to us after the EM-TDR interpretation and inversion. There are mainly four types of features: 
- Machined features: Severe metal loss
- Hand-made irregular shape metal loss
- Machined features: small size metal loss
- Nature corrosion metal loss

Here are the photos of the main feature configurations on the casings: 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture29_1.png) |
|:--:|
| *Machined features: Severe metal loss* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture29_2.png) |
|:--:|
| *Hand-made irregular shape metal loss* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture30.png) |
|:--:|
| *Machined features: small size metal loss* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture31.png) |
|:--:|
| *Nature corrosion metal loss* |

[Back to top](#em-tdr-testing)
#### Ground truth matrix

To put the feature clusters in perspective, we exam the features both in terms of spatial distribution as well as statistical size distribution: 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture32.png) |
|:--:|
| *Top: spatial distribution plot of the 7-inch casing. Bottom: statistical size distribution. The red arrows indicate the small cluster features.* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture33.png) |
|:--:|
| *Top: spatial distribution plot of the 5.5-inch casing. Bottom: statistical size distribution. The red arrows indicate the small cluster features.* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture34.png) |
|:--:|
| *Top: spatial distribution plot of the 4.5-inch casing. Bottom: statistical size distribution. The red arrows indicate the small cluster features.* |

#### Comparision between EM-TDR interpretation results and ground truth

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture35.png) |
|:--:|
| *Comparision between TDR interpretation results and the ground truth. The cold color scheme bars are ground truth. The hot scheme curves are the inversion and interpretation results* |

[Back to top](#em-tdr-testing)
#### EM-TDR interpretation result evaluation

We also evaluate the TDR interpreation results and put the in the statisitcal perspective. We can see most of the missed identified features are either small clusters or at the end of wellbore. 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture36.png) |
|:--:|
| *Result evaluation of 7-inch well: 1* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture37.png) |
|:--:|
| *Result evaluation of 7-inch well: 2* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture38.png) |
|:--:|
| *Result evaluation of 5.5-inch well: 1* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture39.png) |
|:--:|
| *Result evaluation of 5.5-inch well: 2* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture40.png) |
|:--:|
| *Result evaluation of 4.5-inch well: 1* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture41.png) |
|:--:|
| *Result evaluation of 4.5-inch well: 2* |

[Back to top](#em-tdr-testing)
### Preliminary Field Test: MacDonald Island
The preliminary field test at the PG&E facility consists of two part: wellbore test from wellhead, and gathering pipeline test. 

#### Wellbore test: Turner Cut W-1E surface casing 
The location of the wellhead borehole test was conducted at Turner Cut W-1E. This particular well is a decommissioned well and only have the surface casing left. The wellhead (Christmas tree) still left on the wellhead, adding challenge to the TDR measurement. 
| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture42.png) |
|:--:|
| *The location of the Turner Cut W-1E well location* |

This well has previous well logging data publiclly avialbe. The EM-TDR results match the CCL long at most of the locations, indicating casing surrounding affects the EM-TDR signal. 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture43.png) |
|:--:|
| *Comparision between EM-TDR measurement and previous well logging data.* |

#### Gathering pipeline test

The gathering pipeline test was conducted at Turner Cut South station: 
| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture44.png) |
|:--:|
| *Gathering pipeline test location* |

The challenges of this test is that all pipes are somehow connected. In addition, on the wellhead side, the old setup wells were cut off from pipeline, but the new setup wells are not. Here is the comparision between the old and new wellhead:

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture45.png) |
|:--:|
| *Left: Old setup. The tubing is used for withdraw, the casing is used for injection. Right: New setup. The tubing is used for both withdraw and injection. * |

Connection setup:
- Using the casing and tubing of each well as signal input and return path, since they ran parallel.
- In addition, we also used surface cable as return path for comparison.

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture46.png) |
|:--:|
| *Connection setup* |

Challenges: all pipes are somehow connected
We discovered after the later excavation that the pipelines may be connected via the hydraulic lines.
| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture47.png) |
|:--:|
| *Excavation shows all pipes are somehow connected* |

##### Gathering pipeline test results

The EM-TDR results can be further examed by choosing several location to excavated. The EM-TDR shown the reflections from the turning points of the pipelines can be identified. 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture48.png) |
|:--:|
| *Comparision between pipeline turning point on the EM-TDR signal and the excavation site.* |

In addition, we can compare the blueprint of the pipelines and the TDR signal. The reflections from the ends of the pipelines can be clearly seen.

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture49.png) |
|:--:|
| *Comparision between pipeline blueprint and the EM-TDR signals.* |

Because of the paralle layout of the pipeline, we can generate the 2-D map from the EM-TDR signal:
- The end of the pipes are easy to identify.
- The signal seems affected by the condition of the soil.
- The bending of the pipes also were reflected on the EM-TDR signal.

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture50.png) |
|:--:|
| *2-D map generated from the EM-TDR signal* |

We also exam the effects from the surrounding soil condition and terrain. Most of the data have a "low frequency" background signal. 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture51.png) |
|:--:|
| *Seperation of the low-frequency background component from the TDR signal.* |

After seperating the low frequency background signal from the main data, we can see the low-frequency components are somehow coincide with the terrain.

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture53.png) |
|:--:|
| *The low-frequency component coincide with the terrain.* |

This is further comfirmed by the comparision between 2-D plot of the ow-frequency background component and the aerial imagery. The latest public aviable aerial imagery is only at June 2021, which is much earlier than the survey date. During the survey, there was a large soil mount on the ground (see the above image), which was not shown in the aerial imagery.We indicate the location of the mount with dashed box in the following figure.

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture54.png) |
|:--:|
| *Comparision between 2-D plot of the low-frequency background component and the aerial imagery.* |

Finally, we compare the pipeline bluerpint with the 2-D plot with only low-frequency background component as well as with the signal without the low-frequency component. 

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture55.png) |
|:--:|
| *Improved 2-D map generated from the EM-TDR signal. Left: without the low-frequency component. Right: Only with the low-frequency component.* |

- Field tests in vertical borehole shows consistent features from EM-TDR when compared with traditional well logging tools.
- Horizontal pipeline testing and EM-TDR guided excavation suggested sensitivity to pipeline bending effects. Detailed feature identification underway.
- Possible soil compaction/surrounding effects at low frequency on EM-TDR data.

[Back to top](#em-tdr-testing)

### Lab simulated pipeline leakage
In the laboratory test, we use on of the pipe samples from the field. The pipe is 6-ft long, with OD of 4 inch. The location of the pipe sample we used in the test is marked in the box below:

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture56.png) |
|:--:|
| *The location of the pipe sample we used in the lab test.* |

To simulate the water intrusion below the coating, we cut out a 6-cm long, 3-cm width from the coating and put the water-saturated paper towel beneath a new coating. The pipe and setup is shown in the following:

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture57.png) |
|:--:|
| *The “Water intrusion” size: L: 6 cm, W: 3 cm* |

| ![CFER schematic](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture58.png) |
|:--:|
| *The “Water intrusion” set up.* |
