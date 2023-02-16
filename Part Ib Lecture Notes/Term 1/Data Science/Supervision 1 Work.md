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
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5RCG5z7hsBmrF-QFWJFCBf4JNmoCJWWx1qb5NumaUsGp05deuEiDNdkSuJLW2PQmSACOmx8S-k1pBEO1jmKnZGBPbRQ-EKVs2a7Oaabi-_-Z4AFpPJW26YzZLt1ZzFnt.png) 
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
