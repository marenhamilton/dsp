[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```python
import numpy as np
from collections import Counter
from matplotlib import pyplot as plt

sample = sorted(np.random.random(1000))
samplePDF = Counter(num for num in sample)
for key,val in samplePDF.items():
    samplePDF[key] = val/1000
sampleCDF = {}
tprob = 0
for key,val in samplePDF.items() :
    tprob+=val
    sampleCDF[key]=tprob

plt.bar(samplePDF.keys(),samplePDF.values(),width=.001)
plt.plot(sampleCDF.keys(),sampleCDFy.values())

#the issue with the PDF is that you have many values which only occur
#once (at most twice), so you end up with an uninformative barcode-style
#graph, or you have to set bins in order to capture the data better

#the CDF, however, cleanly shows that the distribution is normal

#graphs returned vary between tests; I will not attach them
```
