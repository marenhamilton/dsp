[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
import numpy as np

def Cohen_Effect(g1,g2) :
    n1 = len(g1)
    n2 = len(g2)
    g1avg = np.nanmean(g1)
    g2avg = np.nanmean(g2)
    g1var = np.var(g1)
    g2var = np.var(g2)
    diff = g1avg-g2avg
    pooled_sd = np.sqrt((n1*g1var + n2*g2var)/(n1+n2))
    effect_size = diff/pooled_sd
    return effect_size
    
Cohen_Effect(firsts.totalwgt_lb,others.totalwgt_lb)
#returns -0.08868274594713024
