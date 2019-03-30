[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

```python
class DiffMeansResample(DiffMeansPermute) :
    
    def RunModel(self) :
        resample = np.random.choice(self.pool,size=len(self.pool),replace=True)
        return resample

dataln = firsts.prglngth.values, others.prglngth.values
resampledln = DiffMeansPermute(dataln)
print(f"The p-value for pregnancy length with this model is : {resampledln.PValue()}.")
databw = firsts.totalwgt_lb.values,others.totalwgt_lb.values
resampledbw = DiffMeansPermute(databw)
print(f"The p-value for birthweight for this model is : {resampledbw.PValue()}.")

#With this model, the p-values for birthweight and pregnancy length do not
#seem to change with resampling rather than permutation, so whichever null
#hypothesis we choose in this case is valid
```
