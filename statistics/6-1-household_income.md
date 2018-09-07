[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

```python
import hinc
import hinc2
import scipy.stats
import thinkstats2
import thinkplot
```


```python
df = hinc.ReadData()
```


```python
def analyze_income(df, upper_bound=6.0):
    '''
    Prints median, mean, skewness, Pearson's Skewness, and percent of households reporting income below the mean.

    --------------
    Parameters:
    df: Pandas DataFrame of income data
    upper_bound: Assume log upper bound of income. Eg if upper_bound = 6.0, then we assume no income is above $1e6
    '''

    # Generate sample using hinc2 module
    sample = hinc2.InterpolateSample(df, log_upper=upper_bound)

    # Compute median, mean, skewness, and Pearson skewness
    sample_median = np.median(sample)
    sample_mean = sample.mean()
    sample_skewness = scipy.stats.skew(sample)
    sample_pearson = thinkstats2.PearsonMedianSkewness(sample)

    print('Median of sample: {}'.format(sample_median))
    print('Mean of sample: {}'.format(sample_mean))
    print('Skewness of sample: {}'.format(sample_skewness))
    print('Pearson Skewness of sample: {}'.format(sample_pearson))

    cdf = thinkstats2.Cdf(sample)

    # Use cdf to compute percent of sample with income below the mean
    below_mean = round(cdf.PercentileRank(sample_mean), 2)

    print('\nPercent of households reporting income below mean: {}'.format(below_mean))
```

First we'll analyze the income with an assumed upper bound of __one million dollars__.


```python
analyze_income(df, upper_bound = 6.0)
```

    Median of sample: 4.7094983556124745
    Mean of sample: 4.657585735892018
    Skewness of sample: -0.6413543665661973
    Pearson Skewness of sample: -0.3379202513383129

    Percent of households reporting income below mean: 45.06


Now let's assume the income has an upper bound of __one billion dollars__.


```python
analyze_income(df, upper_bound = 9)
```

    Median of sample: 4.7094983556124745
    Mean of sample: 4.693242859150605
    Skewness of sample: 2.075176115521869
    Pearson Skewness of sample: -0.08082605448735268

    Percent of households reporting income below mean: 48.4


Now let's assume the income is capped at __ten thousand dollars__.


```python
analyze_income(df, upper_bound = 4)
```

    Median of sample: 4.697624192346412
    Mean of sample: 4.633814320386294
    Skewness of sample: -0.9460410641615025
    Pearson Skewness of sample: -0.44004288510414863

    Percent of households reporting income below mean: 44.01


**How do the results change with the upper bound?**

* Median: The median barely changes as we change the upper bound of income
* Mean: The mean increases as we increase the upper bound of income and decreases as we decrease the upper bound of income
* Skewness: When upper bound of income is one million or ten thousand, skewness is negative. When the upper bound of income is one billion dollars, the skewness is positive.
* Pearson Skewness: This statistic is negative for all three upper bounds of income, but is at its greatest when the upper bound of income is one billion dollars.

I was surprised to find that the mean never surpasses the median, even when income is one billion dollars.
