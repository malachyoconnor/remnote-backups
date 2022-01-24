- Supervision 1 Work
    1. 
        - ```python
import numpy as np
import matplotlib.pyplot as plt

def circle_func(x):
	y = ((1 - x**2)**0.5) * np.random.choice([-1, 1], p=[.5, .5]) + np.random.uniform(-0.03, 0.03)
	return x,y

def smile_func(x):
	x = x/2
	y = x**2-0.8+ np.random.uniform(-0.03, 0.03)
	return x,y

def eye_func(x, left):
	x = x/20
	if left:
		x -= 0.4
	else:
		x += 0.4
	y = x*0+0.3 + np.random.uniform(-0.03, 0.03)
	return x,y


def rxy():
	functions = [circle_func, smile_func, lambda x: eye_func(x, True), lambda x: eye_func(x, False)]
	function = functions[np.random.choice([0,1,2,3])]
	return function(np.random.uniform(-1, 1))

results = np.concatenate([rxy() for x in range(1000)]).reshape([1000,2])
print(results)

fig,((ax_x,dummy),(ax_xy,ax_y)) = plt.subplots(2,2, figsize=(4,4), sharex='col', sharey='row', gridspec_kw=dict(height_ratios=[1,2], width_ratios=[2,1]))
dummy.remove()
ax_xy.scatter(results[:,0], results[:,1], s=3, alpha=.1)
ax_x.hist(results[:, 0], density=True, bins=60) # fill in the ???
ax_y.hist(results[:, 1], density=True, bins=60, orientation='horizontal') # fill in the ???
plt.show()
``` 
    2. 
        - density func:
            - $\int_{0}^{u}{u\cdot(1-u)du} = u^2/2 - u^3/3$ 
        - cumulative distribution function:
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5RCG5z7hsBmrF-QFWJFCBf4JNmoCJWWx1qb5NumaUsGp05deuEiDNdkSuJLW2PQmSACOmx8S-k1pBEO1jmKnZGBPbRQ-EKVs2a7Oaabi-_-Z4AFpPJW26YzZLt1ZzFnt.png) 
    3. 
        - pdf = $$\frac{d}{d\theta}(\text{cdf}) = 1_{\theta \ge b_{0}} \cdot (\alpha \cdot \frac{1}{\theta}\cdot (\frac{b_{0}}{\theta})^\alpha )$$ 
        - b.) 
            - $$Pr_\Theta(\theta) = 1_{\theta \ge b_{0}} \cdot (\alpha \cdot \frac{1}{\theta}\cdot (\frac{b_{0}}{\theta})^\alpha )$$ 
            - $$Pr(x_1, x_2,...,x_n | \Theta=\theta) = \left( \frac{1}{\theta} \right)^n$$ 
            - $$Pr(\theta | x_1, x_2, ..., x_n) = 1_{\theta \ge b_{0}} \text{Pareto}(k, \alpha+n)$$ $\text{let} \ c = (\alpha + n) k^{\alpha + n}$  Then $Pr(\theta | x_1, x_2, ..., x_n) = 1_{\theta \ge b_{0}} \ \  c \ \ \frac{1}{\theta} \cdot (\frac{1}{\theta} ^{\alpha + n})$ 
        - c.)
            - $P(\Theta \le \theta) = 0.95$ ⇒ $0.95 = 1 - (\frac{k}{hi})^{(\alpha+n)}$ ⇒ $hi = (0.05)^{-\frac{1}{\alpha + n}} \cdot k$ 
    4. 
        - 
    5. 
        - $X \sim Bin(n, \theta)$  then $Pr(\theta | x=0) = (1-\theta)^n$  
        - $P(\theta | x=0) = \kappa \cdot(Pr(\theta)) \cdot (1 - \theta)^n$ 
        - $1 / \kappa = \int_0^{1/2}{\epsilon (1-\theta)^nd\theta} + \int_{1/2}^{1}{\epsilon (1-\theta)^nd\theta}$ $\rightarrow \kappa = (n+1) / \epsilon$ 
        - $P(\Theta \le 0.5 | x=0) = \kappa\int_0^{1/2}{\epsilon (1 - \theta)^nd\theta} = 1 - \left( \frac{1}{2} \right)^{n+1}$ 
        - This equals a half when n = 0, if epsilon = 0 our results would have been nonsense and the probability would be zero. 
    6. 
        - 
    - 
    - 
    - 
- Supervision 3 Work
    -  _**Question 1:**_  We are given a dataset x1, . . . , xn which we believe is drawn from Normal(µ, σ2 ) where µ and σ are unknown.
        - a.) Find the maximum likelihood estimators µˆ and σˆ: 
$\hat\mu = \frac{1}{n} \sum_i x$ , $\hat \sigma = \frac{1}{n} \sum_i x^2 - \hat\mu^2$ 
        - b.) Find a 95% confidence interval for σˆ, using parametric resampling: ```python
 # x = [x1, x2, ...]
mean, std = np.mean(x), np.std(x) 
n = len(x)

def h(x):
	return np.std(x)

def sample():
	return np.random.normal(mean, std, n)


t = np.array([h(sample()) for x in range(10000)])

interval = np.quantile(t, [0.025, 0.975])
print(interval)
```
    -  _**Question 2:**_   
        - a.) Report a 95% confidence interval for νˆ − µˆ, using parametric sampling: ```python
x = np.array([3,1,5])
y = np.array([2,3])

null_val = np.mean(np.concatenate([x,y]))

def h(x1,y1):
	return -np.mean(x1) + np.mean(y1)

def sample():
	return np.random.poisson(null_val, size=3), np.random.poisson(null_val, size=2)

t = np.array([h(*sample()) for x in range(1000)])
interval = np.quantile(t, [0.025, 0.975])
print("Observed difference in means", np.mean(y) - np.mean(x))
print(interval)

# Observed difference in means -0.5
# [-3.          3.33333333]
```
        - b.) **The above code AND: **  ```python
t_ = np.mean(y) - np.mean(x)
print( 2 * min( np.mean(t_ <= t ) , np.mean( t_ >= t) ))

# 0.801
``` I chose two sided because the difference between the two items can be positive or negative, and whether the difference is positive or negative is important to report. We would like to know whether one chief is having a significantly better or worse impact.
        - c.) ^^Not sure about this, could we go through^^ 
    -  _**Question 3:**_ 
        - a.) ```python
import numpy as np
import pandas
import matplotlib.pyplot as plt
import sklearn.linear_model
import scipy.stats


# Load the dataset
url = 'https://www.cl.cam.ac.uk/teaching/2021/DataSci/data/climate.csv'
climate = pandas.read_csv(url)
climate = climate.loc[(climate.station=='Cambridge') & (climate.yyyy>=1985)].copy()
t = climate.yyyy + (climate.mm-1)/12
temp = (climate.tmin + climate.tmax)/2
# Fit a simple model, and plot it

π = np.pi
X = np.column_stack([np.sin(2*π*t), np.cos(2*π*t), t-2000])
model = sklearn.linear_model.LinearRegression()
model.fit(X, temp)

tnew = np.linspace(1985, 2025, (2025-1985)*12+1)
Xnew = np.column_stack([np.sin(2*π*tnew), np.cos(2*π*tnew), tnew-2000])
tempnew = model.predict(Xnew)


sigma = np.std(temp)

def sample():
	return np.random.normal(tempnew, sigma)

def h(x):
	# The increase in temp between the first and second halves of the dataset averaged
	return (np.mean(x[len(x)//2 : len(x)-1]) - np.mean(x[0: len(x)//2])) / len(x)


samples = np.array([h(sample()) for x in range(10000)])

plt.hist(samples, density=True)
plt.show()
interval = np.quantile(samples, [0.025, 0.975])
print(interval)
``` 
        - outputs: [-0.00038061  0.00329347] which equates to a temperature change of between [-0.4663143317809455, 3.971734353796922] per century.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/G_vvYKWsUWgTdYvAraIN937T7jMUPxJNw3D4J3TBmz3nNBU-JTH7auSCnNNQ5iXccjaU35iQLwfdIXLwOEKOyCo9njrktDsGFCkn_rq7S1kOekWhRvvWFM0VGx6whilm.png) 
        - 
        - b.) ```python
import numpy as np
import pandas
import matplotlib.pyplot as plt
import sklearn.linear_model
import scipy.stats


# Load the dataset
url = 'https://www.cl.cam.ac.uk/teaching/2021/DataSci/data/climate.csv'
climate = pandas.read_csv(url)
climate = climate.loc[(climate.station=='Cambridge') & (climate.yyyy>=1985)].copy()
t = climate.yyyy + (climate.mm-1)/12
temp = (climate.tmin + climate.tmax)/2


# Fit a simple model, and plot it
π = np.pi

tnew = np.linspace(1985, 2025, (2025-1985)*12+1)

# Null hypothesis that the dates are the same, 
# so one variable to be fit is between 2010-2020 OR 1985-1990

datesTnew = ((1985 <= tnew)*(tnew < 1990)+(2010 <= tnew)*(tnew < 2020), (1990 <= tnew)*(tnew< 2000),
             (2000 <= tnew)* (tnew< 2010), (2020 <= tnew)*(tnew <= 2025))

Xnew = np.column_stack([np.sin(2*π*tnew), np.cos(2*π*tnew), *datesTnew])
tempnew = model.predict(Xnew)
print(model.coef_)
## Result : [-1.06969483 -6.55184889  0.61248728  0.61731992  1.01231992  1.77490753] 

sigma = np.std(temp)

def sample():
    return np.random.normal(tempnew, sigma)

def h(x):
    # The difference between the 1980s and 2010s
    year80s = x[0  * 12:   5 * 12]
    year10s = x[25 * 12 : 35 * 12]
    
    inc80s = ( np.mean( np.split(year80s, 2)[0] ) - np.mean( np.split(year80s, 2)[1] ) ) / len(year80s)
    inc10s = ( np.mean( np.split(year10s, 2)[0] ) - np.mean( np.split(year10s, 2)[1] ) ) / len(year10s)
    return inc10s - inc80s

samples = np.array([h(sample()) for x in range(10000)])

plt.hist(samples, density=True)
plt.show()
interval = np.quantile(samples, [0.025, 0.975])
print([x for x in interval])

real_diff = h(temp)
print(2 * np.min([ np.mean( samples <= real_diff ), np.mean( samples >= real_diff ) ] ))

# result is 0.3566
# 0.3566 > 0.025 - so we accept the null hypothesis
```
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cghRRf1V5S_SBfXGXm3z2enSqJJTBVaVsGimVxqxyFDgShejwOGxpplY3p3TJAtCtYy7roFLeMVgiQ3oZMQJtU-ryvqcMICADe7Yj6ieR2eAocYi6qvgJtE1YDPep0ON.png) 
    - 
    -  _**Question 4:**_ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hYVpdF3g_616zJwKqv979ygzaZOcIulZKc00b9rLC1Q0XfK95UD5FAD1jEM8M_9oY7E_XvZkQZKxynieI8yBYM9FnhwdJmsbCM5OCRB0GyuceMWn4bfnS6JPZB7V2arN.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/buFolL0zHPl78VhEl4Phop6IY4uJk4Ac9lUSJKuUuRLbwKL6oxwf89zKdcsPEMmuA_3amLUO60VeEHNEGdCBB8Fcqfp8paXwlMQr9LX1_UHtiPrQzZ7KFNtbM45rSxB-.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/DXf6ni8P8txwwpykxN7UTe8MH86jgdI5DhYhIQitVMSubEMUOyjpPjACyDAXG2qsnmc716I4m-6ywj9P94LEnV8H_zpdZaCq-OsM5dQBRTzlGg42id-QSJqeAMCfPEqy.png) 
    - 
    -  _**Question 5:**_  
        - Consider that the value of theta (success) that makes a run of failures most likely is the lowest possible value, in this case 0.5. 
        - $$(1/2)^n \le 0.05$$$$n \ge \ln(0.05)/\ln(0.5) = 4.32...$$
$$n\ge5$$ 
    -  _**Question 6:**_ 
        - A recent paper Historical language records reveal a surge of cognitive distortions in recent decades by Bollen et al., [https://www.pnas.org/content/118/30/e2102061118.full,](https://www.pnas.org/content/118/30/e2102061118.full,) claims that depression-linked turns of phrase have become more prevalent in recent decades. This paper reports both confidence intervals and null hypotheses. Explain how it is computes them, in particular (1) the readout statistic, (2) the sampling method.
        - The readout statistic is the number of n-grams each year that were labelled as indicative of cognitive distortion, "normalized" by dividing by the number of books published each year.
        - The sampling method was examining millions of books within the Google Books database and calculating the readout statistic. When generating the Null data that formed the null hypothesis they generated 10000 sets of 241 randomly chosen n-grams for each year.
        - The null hypothesis would then be that the readout statistic of the values sampled from Google books is the same as the Null data.
        - Confidence intervals were calculated by generating 10000 different random samples of CDS engrams from the google database for each year - the interval is then between the lowest and highest percentage of CDS detected from those 10000 random samples.
        - longitudinal prevalence of hundreds of short sequences of one to five words (n-grams), labeled cognitive distortion schemata (CDS), that were designed by a team of CBT experts, computational linguists, and bilingual native speakers and externally validated by a panel of CBT experts  
        - To account for changes in publication volume, for each CDS n-gram we define its prevalence in a given year as the number of times it occurred that year in the Google Books data divided by the total volume published  
        - against a null model of 10,000 sets of 241 randomly chosen n-gram  
        - sets of random n-grams were sampled from all n-grams in the respective English, Spanish, and German Google n-gram corpus such that they have the same number of 1- to 5-gram  
- 
- 
