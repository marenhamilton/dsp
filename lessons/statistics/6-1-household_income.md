[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

```python
def raw_moment(xs,k) :
    #if k=1, is mean
    return sum(x**k for x in xs)/len(xs)
def centre_moment(xs,k) :
    #if k=2, is variance
    mean = raw_moment(xs,1)
    return sum((x-mean)**k for x in xs)/len(xs)
def stand_moment(xs,k) :
    #if k=3, gives measure of skewness
    std = (centre_moment(xs,2))**.5
    return centre_moment(xs,k) / std**k
def skewness(xs) :
    return stand_moment(xs,3)
def pears_skew(xs) :
    median = thinkstats2.Cdf(xs).Value(.5)
    mean = raw_moment(xs,1)
    std = (centre_moment(xs,2))**.5
    return 3*(mean-median)/std

median = round(cdf.Value(.5),2)
mean = round(raw_moment(sample,1),2)
skewness = round(skewness(sample),2)
p_skew = round(pears_skew(sample),2)
b_mean = .66
print(f'Median = {median}\nMean = {mean}\nSkewness = {skewness}\n'
      f'Pearson Skewness = {p_skew}\nPercent below the mean : {b_mean}')
      
#returns :
#Median = 51226.45
#Mean = 74278.71
#Skewness = 4.95
#Pearson Skewness = 0.74
#Percent below the mean : 0.66



#Without the upper bound on income, the percent below the mean would be even more as extremely high incomes would further inflate the mean value
