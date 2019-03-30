[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

```python
import numpy as np
import math
import matplotlib.pyplot as plt

def RMSE(actual,estimates) :
    e2 = [(estimate-actual)**2 for estimate in estimates]
    mse = np.mean(e2)
    return math.sqrt(mse)
def EstimateExp(n,m,lam) :
    means = []
    for _ in range(m):
        xs = [np.random.exponential(scale=lam,size=n)]
        xbar = np.mean(xs)
        means.append(xbar)
    return means
def StdErr(actual,estimates) :
    return RMSE(actual,estimates)
def CI(lower,upper,estimates) :
    return (round(np.percentile(estimates,lower),2),round(np.percentile(estimates,upper),2))
def nexperiment(n_lst):
    lam = 2
    m = 1000
    std_errs = []
    for n in n_lst :
        expmeans = EstimateExp(n,m,lam)
        std_errs.append(StdErr(lam,expmeans))
    plt.plot(n_lst,std_errs)
    

#running actual values
lam  = 2
n = 10
m = 1000

means = EstimateExp(n,m,lam)
cdf = np.cumsum(sorted(means))/sum(means)
plt.plot(sorted(means),cdf)
plt.xlabel('sample mean')
plt.ylabel('CDF')
plt.title('Sampling Distribution')
plt.show()
stderr = StdErr(lam,means)
ci = CI(5,95,means)
print(f'The standard error is {stderr}.\nThe 90% confidence inverval is {ci}.\n\n\n')

nexperiment([2,5,10,25,50,100,250,500,750,1000])

#returns slightly different values each time, so I won't attach graphs or outputs
```
