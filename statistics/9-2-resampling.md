[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

```python
import hypothesis
import first
import thinkstats2
import thinkplot
import nsfg
```


```python
class DiffMeansResample(hypothesis.DiffMeansPermute):

    def RunModel(self):
        xs = np.random.choice(self.pool, self.n, replace=True)
        ys = np.random.choice(self.pool, self.m, replace=True)
        return xs, ys
```


```python
live, firsts, others = first.MakeFrames()
```


```python
firsts_prglngth = firsts.prglngth.values
others_prglngth = others.prglngth.values[:len(firsts_prglngth)]
prglngth_data = [firsts_prglngth, others_prglngth]
```


```python
firsts_totalwgt = firsts.totalwgt_lb.dropna().values
others_totalwgt = others.totalwgt_lb.dropna().values[:len(firsts_totalwgt)]

totalwgt_data = [firsts_totalwgt, others_totalwgt]
```


```python
def compare_test_methods(firsts, others):
    '''
    Prints statistics produced by resampling hypothesis test method, then prints statistics produced
    by the permutation hypothesis testing method.
    ---------------
    Parameters:
    firsts: array-like object of first group (first babies)
    others: array-like object of other group (non-first babies)
    '''

    data = firsts, others
    ht = DiffMeansResample(data)
    pval = ht.PValue()
    print('Diff means resample method:')
    print('p value: {}'.format(pval))
    print('Actual difference in means: {}'.format(ht.actual))
    print('Max test statistic: {}'.format(ht.MaxTestStat()))

    # Now permutation method
    ht = hypothesis.DiffMeansPermute(data)
    pval = ht.PValue()
    print('\nDiff means permutation method:')
    print('p value: {}'.format(pval))
    print('Actual difference in means: {}'.format(ht.actual))
    print('Max Test statistic: {}'.format(ht.MaxTestStat()))
```


```python
compare_test_methods(prglngth_data[0], prglngth_data[1])
```

    Diff means resample method:
    p value: 0.128
    Actual difference in means: 0.08769544527532247
    Max test statistic: 0.16383412644459838

    Diff means permutation method:
    p value:0.117
    Actual difference in means: 0.08769544527532247
    Max Test statistic: 0.20371629277136094



```python
compare_test_methods(birthwgt_data[0], birthwgt_data[1])
```

    Diff means resample method:
    p value: 0.0
    Actual difference in means: 0.12476118453549034
    Max test statistic: 0.09844255167113847

    Diff means permutation method:
    p value:0.0
    Actual difference in means: 0.12476118453549034
    Max Test statistic: 0.09382699805486272


Both methods produce almost identical statistics for birth weight data and pregnancy length data.
