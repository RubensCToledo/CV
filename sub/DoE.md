# Design of Experiments projects
When dealing with experiments, it is not always possible to obtain a large number of data points or replicates due to constraints such as cost, time, and logistics. In such cases, DoE techniques prove to be very useful. When performing parametric studies, the goal is to understand how one or more variables affect the outcome of a process. Below, I describe two case studies where I applied different DoE techniques.

## Complete Design $2^k$
In this design, I was investigating a sieving machine for sedimentary rock samples. My goal was to characterize the particle size distribution and their respective amounts in the samples. Data from previous users were inconsistent and did not provide clear guidance on how to set the parameters for sample size, drying time, vibration intensity, and sieving time.

At the time, I was studying DoE techniques and decided to use a full factorial design. Even though it requires a larger number of tests, I believe it is easier to understand and interpret. Below, I present pictures of the machine and the samples used.
Samples           |  Sieving machine
:-------------------------:|:-------------------------:
![quarteamento](https://github.com/user-attachments/assets/9c3bee34-bc24-447c-a377-07713c562a83)  | ![bertel](https://github.com/user-attachments/assets/d5de4930-9f10-4384-88e5-17d685188758)

After consulting various materials, I identified a sample size that aligns with best practices for achieving good results with this machine. The next step was to determine the remaining parameters. I came up with the following setup:
Parameter              | Coded variable | Negative level | Positive level
:---------------------:|:--------------:|:--------------:|:--------------:
Drying time (h)        | A              | 2              | 24
Vibration intensity (%)| B              | 2              | 80
Sieving time (min)     | C              | 3              | 15

The final design involved 3 parameters at 2 levels each. A total of 8 unique experiments were conducted, with each experiment repeated 3 times, totaling 24 runs. The experimental matrix, including the results, is shown below:

| Sample | Drying time (h) | Vibration intensity (%) | Sieving time (min) | % of mass replicates 1 | % of mass replicates 2 | % of mass replicates 3 | Mean  | s²   |
|--------|-----------------|-------------------------|--------------------|------------------------|------------------------|------------------------|-------|------|
| 1      | 2               | 20                      | 3                  | 55.2                   | 60.6                   | 58.7                   | 58.2  | 7.5  |
| 2      | 24              | 20                      | 3                  | 58.1                   | 54.5                   | 51.5                   | 54.7  | 11.1 |
| 3      | 2               | 80                      | 3                  | 61.7                   | 61.0                   | 61.8                   | 61.5  | 0.2  |
| 4      | 24              | 80                      | 3                  | 60.2                   | 60.1                   | 61.2                   | 60.5  | 0.3  |
| 5      | 2               | 20                      | 15                 | 55.8                   | 58.1                   | 59.7                   | 57.9  | 3.7  |
| 6      | 24              | 20                      | 15                 | 56.1                   | 56.3                   | 55.7                   | 56.0  | 0.2  |
| 7      | 2               | 80                      | 15                 | 62.3                   | 61.6                   | 61.9                   | 62.0  | 0.1  |
| 8      | 24              | 80                      | 15                 | 61.8                   | 61.2                   | 61.9                   | 61.6  | 0.1  |

By analyzing the effect of each parameter on the final results, as shown in the table below:
| Parameter order | Parameter | Effect | Relevancy    |
|-----------------|-----------|--------|--------------|
| 1°              | A         | -1.68  | not relevant |
|                 | B         | 4.72   | relevant     |
|                 | C         | 0.65   | not relevant |
|                 | AB        | 1.00   | not relevant |
| 2°              | BC        | 0.12   | not relevant |
|                 | AC        | 0.59   | not relevant |
| 3°              | ABC       | -0.26  | not relevant |

These results have shown me that the only factor impacting my tests was the vibration intensity, which allowed me to conduct the tests more quickly and with less concern about drying the samples. While the DoE technique is very useful, careful consideration and critical analysis are essential when making decisions. Below is a image of the analysis conducted for 7 replicates, following the parameters identified in this study.
![3eb0e1fe8393faaf3639dab83fdf1cbac24a83e4](https://github.com/user-attachments/assets/b19cbe85-3e4d-4329-9963-83980a2bcbf2)
In this case, the fluctuation observed at lower particle sizes is acceptable. However, it's important to remember that this analysis was based on 3 replicates, which may not fully capture the complete effect of each variable. Increasing the number of replicates could result in more than 100 tests, which is typically not feasible for various reasons. For this reason, more robust techniques should be applied when conducting parametric studies.

A example code of this technique can be seen on here
## Composite Central Design

In this project I was trying to optimize 





