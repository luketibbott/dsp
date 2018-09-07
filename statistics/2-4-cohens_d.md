[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
import thinkstats2
import nsfg

preg = nsfg.ReadFemPreg()

live = preg[preg.outcome == 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

firsts_wgt = firsts.totalwgt_lb.mean()
others_wgt = others.totalwgt_lb.mean()

print(firsts_wgt - others_wgt)
```
-0.12476118453549034

Non-first babies are .125 lbs heavier on average

```
thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
```
-0.088672927072602

This effect size is about three times larger than the difference in pregnancy length effect size, but still considered small. According to [Wikipedia](https://en.wikipedia.org/wiki/Effect_size#Cohen's_d) this is somewhere between "very small" and "small."
