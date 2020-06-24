[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

Both of the graphs shown below, display a uniform distribution.  The left graph might seem slightly confusing and hard to read, since it is just a block, however when looking at a uniform distribution pdf or pmf, the block is exactly what we should see since each value has an equal, or uniform, chance of being chosen.  The right graph shows the cdf distribution, and backs up the uniform distribution we saw from the pmf.  This can be seen in the cdf since it is a linear graph.  A cdf tells us the probabilty of values in that distribution falling at or below that specific value, therefore at our max value we should see a result of one, which we do see.  We want a linear graph to show us the distribution is uniform because this tells us that the increase in probability at each increased value is the same, this would be the slope.  The code for this problem can be seen below the two plots.  
![Valid XHTML](https://github.com/lucy-allen/project1/blob/master/ch4ex2pmfgraph.png)
![Valid XHTML](https://github.com/lucy-allen/project1/blob/master/ch4ex2cdfgraph.png)
```{python}
import numpy as np
import thinkstats2
import thinkplot

dist = np.random.random(1000)

pmf = thinkstats2.Pmf(dist)
thinkplot.pmf(pmf)
thinkplot.Config(xlabel='Numbers', ylabel='PMF')

cdf = thinkstats2.Cdf(dist)
thinkplot.cdf(cdf)
thinkplot.Config(xlabel='Numbers', ylabel='CDF')
```
