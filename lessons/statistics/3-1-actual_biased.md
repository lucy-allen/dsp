[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

While looking at the `NUMKDHH` variable, it is really interesting to see the differences in the actual vs. biased distribution results.  Looking at the plot of these two distributions, shown below, you see the biased plot has a max at 2 children in the household, while the actual max is at zero children.  This also shows an overrepresented amount of children for all values greater than or equal to that value of 2. This comes about because of the severely underrepresented value of 0, since no one would actually give a response of zero when surveyed about it.  Looking at the mean values for both actual and biased number of children in the family, we see the actual result at 1.02 children, while the biased result shows 2.40 children in the family.  The code for these results can be seen below the plot.   
![Valid XHTML](https://github.com/lucy-allen/project1/blob/master/ch3ex1graph.png)
```{python}
import nsfg
import thinkstats2
import thinkplot

resp = nsfg.ReadFemResp()
pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
biased_pmf = BiasPmf(pmf, label='observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Config(xlabel='Children in Family', ylabel='PMF')
print('Actual mean', pmf.Mean())
print('Observed mean', biased_pmf.Mean())
```
