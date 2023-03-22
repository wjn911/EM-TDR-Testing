# EM-TDR-Testing

| Task Name | Description | Progress |
| ------------- | ------------- | ------------- |
| [Numerical Scheme](#numerical-scheme-25-d-approach)  | Brief introduction of the 2.3-D numerical scheme  | Finished  |
| Content Cell  | Content Cell  | Content Cell  |


# Numerical Scheme: 2.5-D approach

In most of the case, the pipeline has relative thin pipe wall but very long length, making it is very expensive to simulate in full 3-D scenario. To compensate such dilema, we addopt the 2.5-D approach: First, we simulate the cross-section of every possiable pipe condition. As result, we can calculate the characteristic impednace per unit length of these conditions. The cross-section simulation is shown in the following figure as an example: 

![characteristic impednace calculation](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture1.png)

Secondly, we assemble these sections into 1-D model and simulate the EM-TDR response. 

![2.5-D approach](https://github.com/wjn911/EM-TDR-Testing/blob/main/Figures/Picture2.png)
