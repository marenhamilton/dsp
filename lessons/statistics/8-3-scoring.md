[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

```python
import matplotlib.pyplot as plt
import numpy as np
import math

def RMSE(actual,estimates) :
    e2 = [(estimate-actual)**2 for estimate in estimates]
    mse = np.mean(e2)
    return math.sqrt(mse)
def ManyGames(m,lam) :
    Ls = []
    for _ in range(m) :
        Ls.append(SimulateGame(lam))
    plt.plot(sorted(Ls),np.cumsum(sorted(Ls))/sum(Ls))
    plt.axvline(x=np.percentile(Ls,5),linestyle='--',c = 'grey',linewidth=.5,label='5th and 95th percentile')
    plt.axvline(x=np.percentile(Ls,95),linestyle='--',c='grey',linewidth=.5,)
    plt.legend()
    plt.xlabel('Goals Scored')
    plt.ylabel('CDF')
    plt.title('Sampling Distribution')
    plt.show()
    errs = [L-lam for L in Ls]
    print(f'The mean error is {np.mean(errs)}.')
    print(f'The standard error is {RMSE(lam,Ls)}.')
ManyGames(100000,5)

#This way of sampling appears not to be biased, as the sampling error
#decreases as the number of games increases, so the estimator seems to 
#be unbiased

#The sampling error increases as lam increases
```
