[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

``python
import scipy.stats
```


```python
mu = 178
sigma = 7.7

male_pop = scipy.stats.norm(loc=mu, scale=sigma)
```


```python
blue_min = (5*12 + 10)*2.54
blue_max = (6*12 + 1)*2.54
```


```python
male_pop.cdf(blue_max) - male_pop.cdf(blue_min)
```




    0.34274683763147457



34% of the U.S. male population is in the range required to join the Blue Man Group.
