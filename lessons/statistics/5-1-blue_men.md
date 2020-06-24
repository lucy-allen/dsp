[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

Using the data from the BRFSS about men's heights and the knowledge of this being a relatively normal distribution with the mean being 178 cm and the standard deviation being 7.7 cm we can create the distribution and gain information on it.  In order to find the percentage of males that can join the Blue Man Group, knowing that the max height accepted is 6'1'' and the min height is 5'10'' all we need to do is compute the percentage of males that fall in that height range.  This can easily be done with a cdf since we know the cdf tells us the percent of values at or below a given number.  So if we subtract these two cdf values we receive a result of 0.34, telling us that approximately 34% of the US male polution falls in the height range to be able to join the Blue Man Group.  Code for this problem is found below.  
```{python}
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

print(dist.cdf(185.42)-dist.cdf(177.8))
```
