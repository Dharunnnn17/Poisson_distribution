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
```
DEVELOPED BY:DHARUN ARULSELVAN
REG NO:212224220024
```
```
import numpy as np
import math
import scipy.stats

L = [int(i) for i in input().split()]
N = len(L)
M = max(L)

X = list(range(M+1))
f = [L.count(i) for i in X]
Sff = np.sum(f)

mean = sum([X[i] * f[i] for i in range(M+1)]) / Sff

print("X   P(X=x)  Obs.Fr  Exp.Fr   xi")
print("----------------------------------")

p = []
E = []
xi = []

for x in X:
    px = math.exp(-mean) * mean**x / math.factorial(x)
    exp_fr = px * Sff
    chi_comp = ((f[x] - exp_fr) ** 2) / exp_fr if exp_fr != 0 else 0

    p.append(px)
    E.append(exp_fr)
    xi.append(chi_comp)

    print(f"{x:<3}{px:<8.3f}{f[x]:<8}{exp_fr:<8.2f}{chi_comp:<8.2f}")

print("----------------------------------")
cal_chi2_sq = np.sum(xi)
print(f"Calculated value of Chi square is {cal_chi2_sq:.2f}")

df = M - 1
table_chi2 = scipy.stats.chi2.ppf(1 - 0.01, df=df)
print(f"Table value of chi square at 1% level is {table_chi2:.2f}")

if cal_chi2_sq < table_chi2:
    print("The given data can be fitted to a Poisson Distribution at 1% LOS")
else:
    print("The given data cannot be fitted to a Poisson Distribution at 1% LOS")
```

# Output : 
<img width="798" height="616" alt="image" src="https://github.com/user-attachments/assets/03bc54e2-e16e-4384-92c0-c9dcbe6028ac" />



# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
