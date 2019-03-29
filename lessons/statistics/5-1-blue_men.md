[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)
```python
mu = 178/2.54
sigma = 7.7/2.54
heights = scipy.stats.norm(loc=mu,scale=sigma)
print(f'Approximately {round((heights.cdf(73)-heights.cdf(70))*100,2)}% '
      'of the US male population is the correct height for the blue man group.')
# returns :
#Approximately 34.27% of the US male population is the correct height for the blue man group.
```
