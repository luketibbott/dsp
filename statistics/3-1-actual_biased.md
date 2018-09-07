[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

```
import thinkstats2
import nsfg
import probability

resp = nsfg.ReadFemResp()

pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')
thinkplot.Hist(pmf)

pmf_biased = probability.BiasPmf(pmf, label='biased')
thinkplot.Hist(pmf_biased)

print('Unbiased mean: {} \nBiased mean: {}'.format(pmf.Mean(), pmf_biased.Mean()))
```

Unbiased pmf:

![image](statistics/unbiased_pmf.png)

Biased pmf:

![image](statistics/biased_pmf.png)

Unbiased mean: 1.024205155043831
Biased mean: 2.403679100664282
