# EM-TDR-Testing

| Task Name | Description | Progress |
| ------------- | ------------- | ------------- |
| [Numerical Scheme](#numerical-scheme-25-d-approach)  | Brief introduction of the 2.3-D numerical scheme  | Finished  |
| [Numerical simulation test](#numerical-simulation-test) | 2-D pipe cross-section in different scenarios:<br>[Dis-bond coating with intact coating and metalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-intact-coating-no-corrosion) <br>[Dis-bond coating with intact/ broken coating and intact matalic pipe](#numerical-simulation-scenario-1-dis-bond-coating-broken-coating-no-corrosion) | Finished  |


# Numerical Scheme: 2.5-D approach

In most of the case, the pipeline has relative thin pipe wall but very long length, making it is very expensive to simulate in full 3-D scenario. To compensate such dilema, we addopt the 2.5-D approach: First, we simulate the cross-section of every possiable pipe condition. As result, we can calculate the characteristic impednace per unit length of these conditions. The cross-section simulation is shown in the following figure as an example: 

| ![characteristic impednace calculation](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture1.png) |
|:--:|
| *Example of calculating the characteristic impednace of the unit length and simulation of the 2-D cross-section* |

Secondly, we assemble these sections in the longitudinal into a 1-D model and simulate the EM-TDR response. 

| ![2.5-D approach](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture2.png) |
|:--:|
| *Assemble the 2-D cross-sections into 1-D model in longitudinal direction* |

# Numerical simulation test
## Numerical simulation Scenario 1: Dis-bond coating, intact coating, no corrosion
In this case, the intruding fluid is mostly air. A little air-packet is form between coating layer and metalic pipe. We also demonstrate varies thickness of the intruding air layer.
The result is shown below: 

| ![Dis-bond pipe](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture3.png) |
|:--:|
| *Numerical simulation of the dis-bond coating filled with air. The cross-sections illustrate the voltage potential field as well as the electric field* |

## Numerical simulation Scenario 1: Dis-bond coating, broken coating, no corrosion

Here we demonstrate a example of 2-D cross-section simulation of water intrusion scenario with both intact coating as well as broken coating: 
| ![Dis-bond pipe](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture4.png) |
|:--:|
| *Numerical simulation of the dis-bond coating filled with water. Here it is showing the coating is not broken, broken width of 10&deg;, and 20&deg;, respectively. The cross-sections illustrate the voltage potential field as well as the electric field* |
