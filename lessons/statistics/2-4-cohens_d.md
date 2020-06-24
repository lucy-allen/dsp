[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Using Cohen's D, the effect size of childs weight is -0.089.  This means that the average weight of first children is smaller than that of other children. The Cohen's D for pregnancy length was 0.029, so the average pregnancy length for the first child is longer than the other children.  The negative vs. positive number value here shows whether the average value, for the `group1` input, is larger or smaller.  The absolute value would then show us by how much that difference is.  So this shows a larger difference in the child's weight than the pregnancy length.  The code used to come to this result can be found below, and the result about pregnancy length came directly from the textbook. 
``` {python}
import nsfg
import math

preg = nsfg.ReadFemPreg()

live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1] 
others = live[live.birthord != 1]

print(firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean())

def CohenEffectSize(group1, group2): 
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2) 
    d = diff / math.sqrt(pooled_var)
    return d

print(CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb))
```
