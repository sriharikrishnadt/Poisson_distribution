# Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :

![image](https://user-images.githubusercontent.com/103921593/230282876-f4a5afbf-cac1-4648-a1b0-c78840638a8e.png)

# Program :

 ```python

import numpy as np
import math
from scipy.stats import chi2

# Number of arrivals (x)
x = np.array([0, 1, 2, 3, 4, 5])

# Observed frequencies
fo = np.array([8, 15, 20, 12, 4, 1])

# Total frequency
N = np.sum(fo)

# Mean of the distribution (λ)
mean = np.sum(x * fo) / N

print("Mean (λ) =", round(mean, 4))

# Expected frequencies using Poisson distribution
fe = []

for i in x:
    p = (math.exp(-mean) * (mean ** i)) / math.factorial(i)
    fe.append(N * p)

fe = np.array(fe)

print("\nObserved Frequencies :", fo)
print("Expected Frequencies :", np.round(fe, 2))

# Chi-Square Test
chi_square = np.sum(((fo - fe) ** 2) / fe)

print("\nCalculated Chi-Square Value =", round(chi_square, 4))

# Degree of freedom
df = len(x) - 2

# Table value at 5% level of significance
table_value = chi2.ppf(0.95, df)

print("Table Chi-Square Value =", round(table_value, 4))

# Result
if chi_square < table_value:
    print("\nResult : Poisson distribution is fitted for the given data.")
else:
    print("\nResult : Poisson distribution is NOT fitted for the given data.")
 ```

# Output : 

<img width="719" height="212" alt="image" src="https://github.com/user-attachments/assets/48dce422-9cec-4290-b01f-ed9ad4332d62" />

# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
