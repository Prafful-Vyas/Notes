# 2.1 Introduction

## 2.1.1 What is probability?

**Frequentist interpretation** - In this view, probabilities represent long run frequencies of events that can happen multiple times. E.g. if we flip a coin many times, we expect it to land heads about half the time.

**Bayesian interpretation** - In this view, probability is used to quantify our uncertainty or ignorance about something; hence it is fundamentally related to information rather than repeated trials. In the above statement means we believe the coin is equally likely to land heads or tails on the next toss.

One big advantage of the Bayesian interpretation is that it can be used to model our uncertainty about one-off events that do not have long term frequencies. For example, we might want to compute the probability that the polar ice cap will melt by 2030 CE. This event will happen zero or one times, but cannot happen repeatedly. Nevertheless, we ought to be able to quantify our uncertainty about this event; based on how probable we think this event is; we can decide how to take the optimal action.

## 2.1.2 Types of uncertainty

The uncertainty in our predictions can arise for two fundamentally different reasons.

The first is due to our ignorance of the underlying hidden causes or mechanism generating our data. This is called **epistemic uncertainty**, since epistemology is the philosophical term used to describe the study of knowledge. However, a simple term for this is **model uncertainty**.

The second kind of uncertainty arises from intrinsic variability, which cannot be reduced even if we collect more data. This is sometimes called **aleatoric uncertainty**, although a simpler term would be **data uncertainty**.

## 2.1.3 Probability as an extension of logic

### 2.1.3.1 Probability of an event

We define an **event**, denoted by variable $A$, as some state of the world that either holds or does not hold. The expression $\Pr(A)$ denotes the probability with which you believe event $A$ is true (or the long run fraction of times that $A$ will occur). We require that $0 \le \Pr(A) \le 1$, where $\Pr(A) = 0$ means the event will definitely will not happen, and $\Pr(A) = 1$ means that the event definitely will happen. We write $\Pr(\bar{A})$ to denote the probability of event $A$, not happening; this is defined to be $\Pr(\bar{A}) = 1 - \Pr(A)$.

### 2.1.3.2 Probability of a conjunction of two events

We denote the **joint probability** of events $A$ and $B$ both happening as follows:

$\Pr(A \hspace{1mm} \land \hspace{1mm} B) = \Pr(A,B)$

If $A$ and $B$ are independent events, we have

$\Pr(A,B) = \Pr(A)\Pr(B)$

### 2.1.3.3 Probability of a union of two events

The probability of event $A$ or $B$ happening is given by

$\Pr(A \hspace{1mm} \lor \hspace{1mm} B) = \Pr(A) + \Pr(B) - \Pr(A \hspace{1mm} \land \hspace{1mm} B)$

If the events are mutually exclusive (so they cannot happen at the same time), we get

$\Pr(A \hspace{1mm} \lor \hspace{1mm} B) = \Pr(A) + \Pr(B)$

### 2.1.3.4 Conditional probability of one event given another

we define **conditional probability** of event $B$ happening given that $A$ has occured as follows:

$\Pr(B|A) = \dfrac{\Pr(A,B)}{\Pr(A)}$

This is not defined if $\Pr(A) = 0$, since we cannot condition on an impossible event.

### 2.1.3.5 Independence of events

We say that event $A$ is **independent** of event $B$ if

$\Pr(A,B) = \Pr(A)\Pr(B)$

### 2.1.3.6 Conditional independence of events

We say that events $A$ and $B$ are **conditionally independent** given event $C$ if

$\Pr(A,B|C) = \Pr(A|C)\Pr(B|C)$

This is written as $A \hspace{1mm} \bot \hspace{1mm} B|C$.     Events are often dependent on each other, but may be rendered independent if we condition on the relevant intermediate variables. 

# 2.2 Random Variables

Suppose $X$ represents some unknown quantity of interest, such as which way a dice will land when we roll it, or the temperature outside your house at the current time. If the value of $X$ is unknown and/or could change, we call it a **random variable** or **rv**. The set of possible values, denoted by $\mathcal{X}$, is known as the  **sample space** or **state space**. An **event** is a set of outcomes from a given sample space.

For example, if $X$, represents the face of a dice that is rolled, so $\mathcal{X} = \{1,2,\dots,6\}$, 
the event of “seeing a 1” is denoted $X = 1$, 
the event of “seeing an odd number” is denoted $X \in \{1,3,5\}$, 
the event of “seeing a number between 1 and 3” is denoted $1 \le X \le 3$, etc.

## 2.2.1 Discrete random variables

If the sample space $\mathcal{X}$ is finite or countably infinite, then $X$ is called a **discrete random variable.** In this case, we denote the probability of the event that $X$ has value $x$ by $\Pr(X = x)$. We define the **probability mass function** or **pmf** as a function which computes the probability of events which correspond to setting the rv to each possible value:

$p(x) = \Pr(X = x)$

The pmf satisfies the properties $0 \le p(x) \le 1$ and $\sum_{x \in \mathcal{X}} p(x) = 1$.

If $X$ has a finite number of values, say $K$, the pmf can be represented as a list of $K$ numbers, which we can plot as a histogram. For example, Figure 2.1 shows two pmf’s defined on $\mathcal{X} = \{1,2,3,4\}$.

![image.png](image.png)

On the left we have a uniform distribution, $p(x) = 1/4$, and on the right, we have a degenate distribution, $p(x) = \mathbb{I}(x = 1)$, where $\mathbb{I}()$ is the binary indicator function. Thus the distribution in Figure 2.1(b) represents the fact that $X$ is always equal to the value $1$. (Thus we see that random variables can also be constant.)

## 2.2.2 Continuous random variables

If $X \in \mathbb{R}$ is a real-valued quantity, it is called a **continuous random variable**. In this case, we can no longer create a finite (or countable) set of distinct possible values it can take on. However, there are a countable number of *intervals* which we can partition the real line into. If we associate events with $X$ being in each one of these intervals, we can use these methods discussed above for discrete random variables. Informally speaking, we can represent the probability of $X$ taking on a specific real value by allowing the size of the intervals to shrink to zero, as we show below.

### 2.2.2.1 Cumulative distribution function (cdf)

Define the events $A = (X \le a)$, $B = (X \le b)$ and $C = (a \lt X \le b)$, where $a \lt b$. We have that $B = A \hspace{1mm} \lor \hspace{1mm} C$, and since $A$ and $C$ are mutually exclusive, the sum rules gives

$\Pr(B) = \Pr(A) + \Pr(C)$

and hence the probability of being in interval $C$ is given by

$\Pr(C) = \Pr(B) - \Pr(A)$

In general, we define the **cumulative distribution function** or **cdf** of the rv $X$ as follows:

$P(x) = \Pr(X \le x)$

(Note that we use a capital $P$ to represent the cdf).  Using this, we can compute the probability of being in any interval as follows:

$\Pr(a \lt X \lt b) = P(b) - P(a)$

Cdf’s are monotonically non-decreasing functions. See figure 2.2a for an example, where we illustrate the cdf of a standard normal distribution; see Section 2.6 for details.

![image.png](image%201.png)

### 2.2.2.2 Probability density function (pdf)

We define a **probability density function** or **pdf** as the derivative of the cdf:

$p(x) = \dfrac{d}{dx} P(x)$

(Note that this derivative does not always exist, in which case the pdf is not defined. ) See Figure 2.2b for an example, where we illustrate the pdf of a univariate Gaussian (see Section 2.6 for details).

Given a pdf, we can compute the probability of a continuous variable being in a finite interval as follows:

$\Pr(a \lt X \le b) = \displaystyle\int_a^b p(x)dx = P(b) - P(a)$

As the size of the interval gets smaller, we can write

$\Pr(x \lt X \le x + dx) \approx p(x) dx$

Intuitively, this says the probability of $X$ being in a small interval around $x$ is the density at $x$ times the width of the interval.

### 2.2.2.3 Quantiles

If the cdf $P$ is strictly monotonically increasing, it has an inverse, called the **inverse cdf**, or **percent point function (ppf)**, or **quantile function**.

If $P$ is the cdf of $X$, then $P^{-1}(q)$ is the value $x_q$ such that $\Pr(X \le x_q) = q$; this is called the q’th **quantile** of $P$. The value $P^{-1}(0.5)$ is the **median** of the distribution, with half of the probability mass  on the left, and half on the right. The values $P^{-1}(0.25)$ and $P^{-1}(0.75)$ are the lower and upper **quartiles**.

For example, let $\Phi$ be the cdf of the Gaussian distribution $\mathcal{N}(0,1)$, and $\Phi^{-1}$ be the inverse cdf. Then points to the left of $\Phi^{-1}(\alpha/2)$ contain $\alpha/2$ of the probability mass, as illustrated in Figure 2.2b. By symmetry, points on the right of $\Phi^{-1}(1-\alpha/2)$ also contain $\alpha/2$ of the mass. Hence the central interval $( \Phi^{-1}(\alpha/2), \Phi^{-1}(1 - \alpha/2))$ contains $1- \alpha$  of the mass. If we set $\alpha = 0.05$, the central $95\%$ interval is covered by the range

$( \Phi^{-1}(0.025), \Phi^{-1}(0.975)) = (-1.96, 1.96)$

If the distribution is $\mathcal{N}(\mu,\sigma^2)$, then the $95\%$ interval becomes $(\mu - 1.96\sigma, \mu + 1.96\sigma)$. This is often approximated by writing $\mu \pm 2\sigma$.

![image.png](image%201.png)

## Sets of related random variables

In this section, we discuss distributions over sets of related random variables.

Suppose, to start, that we have two random variables, $X$ and $Y$.  We can define the **joint distribution** of two random variables using $p(x,y) = p(X=x, Y=y)$ for all possible values of $X$ and $Y$.  If both variables have finite cardinality, we can represent the joint distribution as a 2d table, all of whose entries sum to one. For example, consider the following example with two binary variables:

| $p(X, Y)$ | $Y = 0$ | $Y = 1$ |
| --------- | ------- | ------- |
| $X = 0$   | 0.2     | 0.3     |
| $X = 1$   | 0.3     | 0.2     |

If two variables are independent, we can represent the joint as the product of the two marginals. If both variables have a finite cardinality, we can factorize the 2d joint table into a product of two 1d vectors, as shown in Figure 2.3.

![image.png](image%202.png)

Given a joint distribution, we define the **marginal distribution** of an rv as follows:

$p(X=x) = \displaystyle\sum_y p(X=x, Y=y)$

where we are summing over all possible states of $Y$. This is sometimes called the **sum rule** or the **rule of total probability**. We define $p(Y=y)$ similarly. For example, from the above 2d table, we see $p(X=0) = 0.2 + 0.3 = 0.5$ and $p(Y=0) = 0.2 + 0.3 = 0.5$.  (The term “marginal” comes from the accounting practice of writing the sums of rows and columns on the side, or margin, of a table. )

We define the **conditional distribution** of an rv using

$p(Y=y|X=x) = \dfrac{p(X=x, Y=y)}{p(X=x)}$

We can rearrange this equation to get

$p(x,y) = p(x)p(y|x)$

This is called the **product rule.**

By extending the product rule to $D$ variables, we get the **chain rule of probability**:

$p(x_{1:D}) = p(x_1)p(x_2|x_1)p(x_3|x_1,x_2)p(x_4|x_1,x_2,x_3)\dots p(x_D|x_{1:D-1})$

This provides a way to create a high dimensional joint distribution from a set of conditional distributions. We discuss this in more detail in Section 3.6.

## 2.2.4 Independence and conditional independence

We say $X$ and $Y$ are **unconditionally independent** or **marginally independent**, ****denoted $X \hspace{1mm} \bot \hspace{1mm} Y$, if we can represent the joint as the product of two marginals (see figure 2.3), i.e.,

![image.png](image%202.png)

$X \hspace{1mm} \bot \hspace{1mm} Y \iff p(X,Y) = p(X)p(Y)$

In general, we say a set of variables $X_1, \dots,X_n$ is (mutually) **independent** if the joint can be written as a product of marginals for all subsets $\{X_1,\dots,X_m\} \subset \{X_1,\dots,X_n\}$ : i.e.,

$p(X_1,\dots,X_m) = \displaystyle\prod_{i=1}^m p(X_i)$

For example, we say $X_1,X_2,X_3$ are mutually independent if the following conditions hold:

$p(X_1,X_2,X_3) = p(X_1)p(X_2)p(X_3)$, 
$p(X_1,X_2) = p(X_1)p(X_2)$, 
$p(X_2,X_3) = p(X_2)p(X_3)$,
$p(X_1,X_3) = p(X_1)p(X_3)$.

Unfortunately, unconditional independence is rare, because most variables can influence most other variables. However, usually this influence is mediated via other variables rather than being direct. We therefore say $X$ and $Y$ are **conditionally independent** (CI) given Z iff the conditional joint can be written as a product of conditional marginals:

$X \hspace{1mm} \bot \hspace{1mm} Y \hspace{1mm} | \hspace{1mm} Z \iff p(X,Y|Z) = p(X|Z)p(Y|Z)$

We can write this assumption as a graph $X-Z-Y$, which captures the intuition that all the dependencies between $X$ and $Y$ are mediated via $Z$.  By using larger graphs, we can define complex joint distributions; these are known as **graphical models**, and are discussed in Section 3.6.

## 2.2.5 Moments of a distribution

In this section, we describe various summary statistics that can be derived from a probability distribution (either a pdf or a pmf).

### 2.2.5.1 Mean of a distribution

The most familiar property of a distribution is its **mean**, or **expected value**, often denoted by $\mu$. For continuous rv’s, the mean is defined as follows:

$\mathbb{E}[X] = \displaystyle\int_{\mathcal{X}} xp(x)dx$

If the integral is not finite, the mean is not defined; we will see some examples of this later.

For discrete rv’s, the mean is defined as follows:

$\mathbb{E}[X] = \displaystyle\sum_{x \in \mathcal{X}} xp(x)$

However, this is only meaningful if the values of $x$ are ordered in some way (e.g., if they represent integer counts).

Since the mean is a linear operator, we have

$\mathbb{E}[aX + b] = a\mathbb{E}[X] + b$

This is called the **linearity of expectation.**

For a set of $n$ random variables, one can show that the expectation of their sum is as follows:

$\mathbb{E}\left[ \displaystyle\sum_{i=1}^n X_i \right] = \displaystyle\sum_{i=1}^n \mathbb{E}[X_i]$

If they are independent, the expectation of their product is given by

$\mathbb{E} \left[ \displaystyle\prod_{i=1}^n X_i \right] = \displaystyle\prod_{i=1}^n \mathbb{E} [X_i]$

### 2.2.5.2 Variance of a distribution

The **variance** is a measure of the “spread” of a distribution, often denoted by $\sigma^2$. This is defined as follows:

$\mathbb{V}[X] = \mathbb{E}[(X-\mu)^2] = \displaystyle\int (x - \mu)^2p(x)dx$

$\hspace{8.5mm} = \displaystyle\int x^2p(x)dx + \mu^2\displaystyle\int p(x)dx - 2\mu\displaystyle\int xp(x)dx = \mathbb{E}[X^2] - \mu^2$

from which we derive useful result

$\mathbb{E}[X^2] = \sigma^2 + \mu^2$

The **standard deviation** is defined as

$\text{std}[X] = \sqrt{\mathbb{V}[X]} = \sigma$

This is useful since it has the same units as $X$ itself.

The variance of a shifted and scaled version of a random variable is given by

$\mathbb{V}[aX + b] = a^2\mathbb{V}[X]$

If we have a set of *n* independent random variables, the variance of their sum is given by the sum of their variances:

$\mathbb{V}\left[ \displaystyle\sum_{i=1}^n X_i \right] = \displaystyle\sum_{i=1}^n \mathbb{V}[X_i]$

The variance of their product can also be derived, as follows:

$\mathbb{V} \left[ \displaystyle\prod_{i=1}^n X_i \right] = \mathbb{E} \left[ ( \displaystyle\prod_i X_i )^2 \right] - (\mathbb{E} \left[ \displaystyle\prod X_i \right])^2$

$\hspace{23mm} = \mathbb{E} \left[ \displaystyle\prod_i X_i^2 \right] - (\displaystyle\prod_i \mathbb{E}[X_i])^2$ 

$\hspace{23mm} = \displaystyle\prod_i \mathbb{E}[X_i^2] - \displaystyle\prod_i(\mathbb{E}[X_i])^2$

$\hspace{23mm} = \displaystyle\prod_i ( \mathbb{V}[X_i] + (\mathbb{E}[X_i])^2 ) - \displaystyle\prod_i (\mathbb{E}[X_i])^2$

$\hspace{23mm} = \displaystyle\prod_i (\sigma_i^2 + \mu^2_i) - \displaystyle\prod_i \mu_i^2$

### 2.2.5.3 Mode of a distribution

The **mode** of a distribution is the value with the highest probability mass or probability density:

$x^* = \displaystyle \arg\max_x p(x)$

If the distribution is **multinomial**, this may not be unique, as illustrated in Figure 2.4. Furthermore, even if there is a unique mode, this point may not be a good summary of the distribution.

![image.png](image%203.png)

### 2.2.5.4 Conditional moments

When we have two or more dependent random variables, we can compute the moments of one given knowledge of the other. For example, the **law of iterated expectations**, also called the **law of total expectation**, tells us that

$\mathbb{E}[X] = \mathbb{E}_Y[\mathbb{E}[X|Y]]$

To prove this, let us suppose, for simplicity, that $X$ and $Y$ are both discrete rv’s. Then we have

$\mathbb{E}_Y[\mathbb{E}[X|Y]] = \mathbb{E}_Y \left[ \displaystyle\sum_i xp(X=x|Y) \right]$

$\hspace{18.5mm} = \displaystyle\sum_y \left[ \sum_x xp(X=x|Y=y) \right] p(Y=y) = \sum_{x,y} xp(X=x,Y=y) = \mathbb{E}[X]$

To give a more intuitive explanation, consider example. 
Let $X$ be the lifetime duration of a lightbulb, and let $Y$ be the factory the lightbulb was produced in. Suppose $\mathbb{E}[X|Y=1] = 5000$ and $\mathbb{E}[X|Y=2] = 4000$, indicating that factory 1 produces longer lasting bulbs. Suppose factory 1 supplies $60\%$ of the lightbulbs, so $p(Y=1) = 0.6$ and $p(Y=2) = 0.4$. Then the expected duration of a random lightbulb is given by

$\mathbb{E}[X] = \mathbb{E}[X|Y=1]p(Y=1) + \mathbb{E}[X|Y=2]p(Y=2) = 5000 \times 0.6 + 4000 \times 0.4 = 4600$

There is a similar formula for the variance.  In particular, the **law of total variance**, also called the **conditional variance formula**, tells us that

$\mathbb{V}[X] = \mathbb{E}_Y [\mathbb{V}[X|Y]] + \mathbb{V}_Y [\mathbb{E}[X|Y]]$

To see this, let us define the conditional moments, $\mu_{X|Y} = \mathbb{E}[X|Y]$, $s_{X|Y} = \mathbb{E}[X^2|Y]$, and $\sigma^2_{X|Y} = \mathbb{V}[X|Y] = s_{X|Y} - \mu^2_{X|Y}$, which are functions of $Y$  (and therefore are random quantities). Then we have

$\mathbb{V}[X] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2 = \mathbb{E}_Y[s_{X|Y}] - (\mathbb{E}_Y[\mu_{X|Y}])^2$

$\hspace{8.5mm} = \mathbb{E}_Y[\sigma_{X|Y}^2] + \mathbb{E}_Y \left[ \mu_{X|Y}^2 \right] - (\mathbb{E}_Y[\mu_{X|Y}])^2$

$\hspace{8.5mm} = \mathbb{E}_Y [\mathbb{V}[X|Y]] + \mathbb{V}[\mu_{X|Y}]$

To get some intuition for these formulas, consider a mixture of $K$ univariate Gaussians. Let $Y$ be the hidden indicator variable that specifies which mixture component we are using, and let $X = \sum_{y=1}^K \pi_y \mathcal{N}(X|\mu_y, \sigma_y)$.  In figure 2.4 we have $\pi_1 = \pi_2 = 0.5$, $\mu_1 = 0$, $\mu_2 = 2$, $\sigma_1 = \sigma_2 = 0.5$. Thus

$\mathbb{E}[\mathbb{V}[X|Y]] = \pi_1\sigma_1^2 + \pi_2\sigma_2^2 = 0.25$

$\mathbb{V}[\mathbb{E}[X|Y]] = \pi_1(\mu_1 - \bar{\mu})^2 + \pi_2(\mu_2 - \bar{\mu})^2 = 0.5(0-1)^2 + 0.5(2-1)^2 = 0.5 + 0.5 = 1$

So we get the intuitive result that the variance of $X$ is dominated by which centroid it is drawn from (i.e., difference in the means), rather than the local variance around each centroid.

![image.png](image%203.png)

## 2.2.6 Limitations of summary statistics *

# 2.3 Bayes’ Rule

inference - “the act of passing from sample data to generalizations, usually with calculated degrees of certainty”

Bayesian inference → inference methods that represents “degrees of certainty” using probability theory, and which leverage **Bayes’ Rule**, to update the degree of certainty given data.

Bayes’ rule is a formula for computing the probability distribution over possible values of an unknown quantity $H$ given some observed data $Y = y$ :

$\displaystyle p(H=h|Y=y) = \frac{p(H=h)p(Y=y|H=h)}{p(Y=y)}$

This follows automatically from the identity

$p(h|y)p(y) = p(h)p(y|h) = p(h,y)$

 which itself follows from the **product rule of probability.**

 $p(H)$ represents what we know about possible values of $H$ before we see any data; this is called the **prior distribution.** (If $H$ has $K$ possible values, then $p(H)$ is a vector of $K$ probabilities, that sum to 1).
 
 $p(Y|H=h)$ represents the distribution over the possible outcomes $Y$ we expect to see if $H=h$; this is called the **observation distribution.** When we evaluate this at a point corresponding to the actual observations, $y$, we get the function $p(Y=y|H=h)$, which is called the **likelihood.** (Note that this is a function of $h$, since $y$ is  fixed, but it is not a probability distribution, since it does not sum to one.)
 
Multiplying the prior distribution $p(H=h)$ by the likelihood function $p(Y=y|H=h)$ for each $h$ gives the unnormalized joint distribution $p(H=h,Y=y)$. We can convert this into a normalized distribution by dividing by $p(Y=y)$, which is known as **marginal likelihood**, since it is computed by marginalizing over the unknown $H$ (summing over all values of $H$):

$p(Y=y) = \displaystyle \sum_{h' \in \mathcal{H}} p(H=h')p(Y=y|H=h') = \sum_{h' \in \mathcal{H}} p(H=h', Y=y)$

Normalizing the joint distribution by computing $p(H=h, Y=y)/p(Y=y)$ for each $h$ gives the **posterior distribution** $p(H=h|Y=y)$; this represents our new **belief state** about the possible values of $H$.
We can summarize Bayes rule in words as follows:

posterior $\propto$ prior $\times$ likelihood

We are ignoring the denominator, which is just a constant, independent of $H$. Using Bayes rule to update a distribution over unknown values of some quantity of interest, given relevant observed data, is called **Bayesian inference**, or **posterior inference**, or just be called **probabilistic inference**.

## 2.3.1 Example: Testing for COVID-19

Let $H=1$ be the event that you are infected,
and $H=0$ be the event that you are not infected.
Let $Y=1$ if the test is positive,
and $Y=0$ if the test is negative. 

We want to compute $p(H=h|Y=y)$, for $h \in \{0,1\}$, where $y$ is the observed test outcome. (We will write the distribution of values $[p(H=0|Y=y), p(H=1|Y=y)]$ as $p(H|y)$, for brevity.) We can think of this as a form of **binary classification**, where $H$ is unknown class label, and $y$ is the feature vector.

First we must specify the likelihood. This quantity obviously depends on how reliable the test is. There are two key parameters.
- The **sensitivity** (aka **true positive rate**) is defined as $p(Y=1|H=1)$, i.e., the probability of a positive test given that the truth is positive. The **false negative rate** is defined as one minus the sensitivity.
- The **specificity** (aka **true negative rate**) is defined as $p(Y=0|H=0)$, i.e., the probability of a negative test given that the truth is negative. The **false positive rate** is defined as one minus the specificity. We summarize all these quantities in a table.

![[Pasted image 20250724142312.png]]

Next we specify the prior, The quantity $p(H=1)$ represents the **prevalence** of the disease in the area in which you live. We set this to $p(H=1) = 0.1$ (i.e., 10%), which was the prevalence in New York City in Spring 2020. 

Now suppose you test positive. We have

$p(H=1|Y=1) = \dfrac{P(Y=1|H=1)p(H=1)}{P(Y=1|H=1)p(H=1) + p(Y=1|H=0)p(H=0)}$

$\hspace{3cm} = \dfrac{\text{TPR} \times \text{prior}}{\text{TPR} \times \text{prior} + \text{FPR} \times (1-\text{prior})}$

$\hspace{3cm} = \dfrac{0.875 \times 0.1}{0.875 \times 0.1 + 0.025 \times 0.9} = 0.795$

So there is a 79.5% chance you are infected.

Now suppose you test negative, The probability you are infected is given by

$p(H=1|Y=0) = \dfrac{p(Y=0|H=1)p(H=1)}{p(Y=0|H=1)p(H=1) + p(Y=0|H=0)p(H=0)}$

$\hspace{3cm} = \dfrac{\text{FNR} \times \text{prior}}{\text{FNR} \times \text{prior} + \text{TNR} \times (1-\text{prior})}$

$\hspace{3cm} = \dfrac{0.125 \times 0.1}{0.125 \times 0.1 + 0.95 \times 0.9} = 0.014$

So there is just a 1.4% chance you are infected.

Nowadays, COVID prevalence is much lower. Suppose we repeat these calculations using a base rate of 1%; now the posteriors reduce to 26% and 0.13% respectively.

The fact that you only have a 26% chance of being infected with COVID, even after a positive test, is very counter-intuitive. The reason is that a single positive test is more likely to be a false positive than due to the disease, since the disease is rare.

To see this suppose we have a population of $100,000$ people, of whom $1000$ are infected. Of those who are infected, $0.875 \times 1000 = 875$  test positive, and 
of those who are uninfected, $0.025 \times 99,000 = 2475$ test positive.
Thus the total number of positives is $875+2475 = 3350$, so the posterior of being infected given a positive test is $875/3350 = 0.26$.

## 2.3.2 Example: Monty Hall problem

Imagine a game show with the following rules: There are three doors, labeled 1, 2, 3. A single prize (e.g., a car) has been hidden behind one of them. You get to select one door. Then the gameshow host opens one of the other two doors (not the one you picked), in such a way as to not reveal the prize location. At this point, you will be given a fresh choice of door: you can either stick with your first choice, or you can switch to the other closed door. All the doors will then be opened and you will receive whatever is behind your final choice of door.

For example, suppose you choose door 1, and the gameshow host opens door 3, revealing nothing behind the door, as promised. Intuitively, it seems it should make no difference, since your initial choice of door cannot influence the location of the prize. However, the fact that the host opened door 3 tells us something about the location of the prize, since he made his choice conditioned on the knowledge of the true location and on your choice. As we show below, you are in fact twice as likely to win the prize if you switch to door 2.

To show this. Let $H_i$ denote the hypothesis that the prize is behind door $i$. We make the following assumptions: the three hypotheses $H_1$, $H_2$, and $H_3$ are equiprobable a $priori$, i.e.,

$P(H_1) = P(H_2) = P(H_3) = \dfrac{1}{3}$

The datum we receive, after choosing door 1, is either $Y=3$ and $Y=2$ (meaning door 3 or 2 is opened, respectively). We assume that these two possible outcomes have the following probabilities. If the prize is behind door 1, then the host selects at random between $Y=2$ and $Y=3$. Otherwise the choice of the host is forced and the probabilities are 0 and 1.

$H_i \to$ prize is behind door $i$
$Y \to$ door is opened

$P(Y=2|H_1) = \frac{1}{2} \hspace{1cm} | \hspace{1cm} P(Y=2|H_2) = 0 \hspace{1cm} | \hspace{1cm} P(Y=2|H_3) = 1$
$P(Y=3|H_1) = \frac{1}{2} \hspace{1cm} | \hspace{1cm} P(Y=3|H_2) = 1 \hspace{1cm} | \hspace{1cm} P(Y=3|H_3) = 0$

Now using Bayes' theorem, we evaluate the posterior probabilities of the hypotheses:

$P(H_i|Y=3) = \dfrac{P(Y=3|H_i)P(H_i)}{P(Y=3)}$

$P(H_1|Y=3) = \dfrac{(1/2)(1/3)}{P(Y=3)} \hspace{0.5cm} | \hspace{0.5cm} P(H_2|Y=3) = \dfrac{(1)(1/3)}{P(Y=3)} \hspace{0.5cm} | \hspace{0.5cm} P(H_3|Y=3) = \dfrac{(0)(1/3)}{P(Y=3)}$

So the contestant should switch to door 2 in order to have the biggest chance of getting the prize. See table for a worked example.

![[Pasted image 20250724150802.png]]

## 2.3.3 Inverse problems*

# 2.4 Bernoulli and binomial distributions

Perhaps the simplest probability distribution is the **Bernoulli distribution**, which can be used to model binary events, as we discuss below.

## Definition

Consider a coin toss, where the probability of event that it lands heads is given by $0 \le \theta \le 1$. Let $Y=1$ denote this event, and let $Y=0$ denote the event that the coin lands tails. Thus we are assuming that $p(Y=1)=\theta$ and $p(Y=0) = 1-\theta$. This is called the **Bernoulli distribution**, and can be written as follows

$Y \sim \text{Ber}(\theta)$

where the symbol $\sim$ means "is sampled from" or "is distributed as", and Ber refers to Bernoulli. The probability mass function (pmf) of this distribution is defined as follows:

$\text{Ber}(y|\theta) = \begin{cases} 1- \theta & \text{if } y=0 \\ \theta & \text{if } y=1 \end{cases}$

$\text{Ber}(y|\theta) = \theta^y(1-\theta)^{1-y}$

The Bernoulli distribution is a special case of the **binomial distribution**. To explain this, suppose we observe a set of $N$ Bernoulli trials, denoted $y_n \sim \text{Ber}(\cdot|\theta)$, for $n = 1:N$ . Concretely, think of tossing a coin $N$ times. Let us define $s$ to be the total number of heads, $s = \sum_{n=1}^N \mathbb{I}(y_n = 1)$. The distribution of $s$ is given by the binomial distribution:

$\text{Bin}(s|N,\theta) = \displaystyle {N \choose s} \theta^s (1-\theta)^{N-s}$

where

$\displaystyle {N \choose k} = \dfrac{N!}{(N-k)!k!}$

is the number of ways to choose $k$ items from $N$ (this is known as the **binomial coefficient**, and is pronounced "N choose k"). See figure below for some examples of the binomial distribution. If $N=1$, the binomial distribution reduces to the Bernoulli distribution.

![[Pasted image 20250724153343.png]]

Example: You flip a coin $N=5$ times. The probability of heads (success) is $\theta = 0.6$. What is the probability of getting exactly $s=3$ heads?

$\displaystyle \text{Bin}(3|5,0.6) = {5 \choose 3} \cdot 0.6^3 \cdot (1-0.6)^{5-3} = 0.3456$

## 2.4.2 Sigmoid (logistic) function

When we want to predict a binary variable $y \in \{0,1\}$ given some inputs $x \in \mathcal{X}$, we need to use a **conditional probability distribution** of the form

$p(y|x,\theta) = \text{Ber}(y|f(x;\theta))$

where $f(x;\theta)$ is some function that predicts the mean parameter of the output distribution. 

To avoid the requirement that $0 \le f(x;\theta) \le 1$, we can let $f$ be an unconstrained function, and use the following model:

$p(y|x,\theta) = \text{Ber}(y|\sigma(f(x;\theta)))$

Here $\sigma()$ is the **sigmoid** or **logistic** function, defined as follows:

$\sigma(a) = \dfrac{1}{1 + e^{-a}}$

where $a= f(x;\theta)$. The term "sigmoid" means S-shaped: see Figure(a) for the plot below. We see that it maps the whole real line to $[0,1]$, which is necessary for the output to be interpreted as a probability (and hence a valid value for the Bernoulli parameter $\theta$). The sigmoid function can be thought of as a "soft" version of the **heaviside step function**, defined by

$H(a) = \mathbb{I}(a \gt 0)$

as shown in Figure(b) below.

![[Pasted image 20250724155240.png]]

Plugging the definition of the sigmoid function into Bernoulli Equation we get

$p(y=1|x,\theta) = \dfrac{1}{1 + e^{-a}} = \dfrac{e^a}{1 + e^a} = \sigma(a)$

$p(y=0|x,\theta) = 1 - \dfrac{1}{1 + e^{-a}} = \dfrac{e^{-a}}{1 + e^{-a}} = \dfrac{1}{1 + e^a} = \sigma(-a)$

The quantity $a$ is equal to the **log odds**, $\log(\frac{p}{1-p})$, where $p=p(y=1|x;\theta)$. To see this, note that

$\log(\dfrac{p}{1-p}) = \log(\dfrac{e^a}{1+e^a} \dfrac{1+e^a}{1}) = \log(e^a) = a$

The **logistic function** or **sigmoid** function maps the log-odds $a$ to $p$:

$p = \text{logistic}(a) = \sigma(a) = \dfrac{1}{1 + e^{-a}} = \dfrac{e^a}{1 + e^a}$

The inverse of this is called the **logit function**, and maps $p$ to the log-odds $a$:

$a = \text{logit}(p) = \sigma^{-1}(p) = \log\left(\dfrac{p}{1-p}\right)$

See table for some useful properties of these functions.

![[Pasted image 20250724162309.png]]

## 2.4.3 Binary logistic regression

In this section, we use a conditional Bernoulli model, where we use a linear predictor of the form $f(x;\theta) = w^\top x + b$. Thus the model has the form

$p(y|x;\theta) = \text{Ber}(y|\sigma(w^\top x + b))$

In other words,

$p(y=1|x;\theta) = \sigma(w^Tx + b) = \dfrac{1}{1 + e^{-(w^\top x + b)}}$

This is called **logistic regression**.

For example consider a 1-dimensional, 2-class version of the iris dataset, where the positive clss is "Virginica" and the negative class is "not Virginica", and the feature $x$ we use is the petal width. We fit a logistic regression model to this and show the results in Figure below. The **decision boundary** corresponds to the value $x^*$ where $p(y=1|x=x^*,\theta) = 0.5$. We see that, in this example, $x^* \approx 1.7$. As $x$ moves away from this boundary, the classifier becomes more confident in its prediction about the class label.

![[Pasted image 20250724174216.png]]

It should be clear from this example why it would be inappropriate to use linear regression for a (binary classification) problem. In such a model, the probabilities would increase above 1 as we move far enough to the right, and below 0 if we move far enough to the left.

# 2.5 Categorical and multinomial distributions

To represent a distribution over a finite set of labels, $y \in \{1,\dots,C\}$, we can use the **categorical** distribution, which generalizes the Bernoulli to $C \gt 2$ values.

## 2.5.1 Definition

The categorical distribution is a discrete probability distribution with one parameter per class:

$\text{Cat}(y|\theta) = \displaystyle \prod_{c=1}^C \theta_c^{\mathbb{I}(y=c)}$

In other words, $p(y=c|\theta) = \theta_c$. Note that the parameters are constrained so that $0 \le \theta_c \le 1$ and $\sum_{c=1}^C \theta_c = 1$; thus there are only $C-1$ parameters.

We can write the categorical distribution in another way by converting the discrete variable $y$ into a **one-hot vector** with $C$ elements, all of which are 0 except for the entry corresponding to the class label.

E.g., if $C=3$, we encode the classes 1,2, and 3 as (1,0,0), (0,1,0), (0,0,1). More generally, we can encode the classes using **unit vectors**, where $y_c$ is all 0s except for dimension $c$. (This is called a **dummy encoding**.) Using one-hot encodings, we can write the categorical distribution as follows:

$\text{Cat}(y|\theta) = \prod_{c=1}^C \theta_c^{y_c}$

Example: $C=4$, and the true class is 3. Then $y = (0,0,1,0)$, so:

$\text{Cat}(y|\theta) = \prod_{c=1}^4 \theta_c^{y_c} = \theta_1^0 \cdot \theta_2^0 \cdot \theta_3^1 \cdot \theta_4^0 = \theta_3$

The categorical distribution is a special case of the **multinomial distribution**. To explain this, suppose we observe $N$ categorical trials, $y_n \sim \text{Cat}(\cdot|\theta)$, for $n=1:N$. Concretely, think of rolling a $C$-sided dice $N$ times. Let us define $y$ to be a vector that counts the number of times each face shows up, i.e., $y_c = N_c = \sum_{n=1}^N \mathbb{I}(y_n = c)$. Now $y$ is no longer one-hot, but it is "multi-hot", since it has non-zero entry for every value of $c$ that was observed across all $N$ trials. The distribution of $y$ is given by the **multinomial distribution**:

$\mathcal{M}(y|N,\theta) = \displaystyle {N \choose {y_1 \dots y_C}} \prod_{c=1}^C \theta_c^{y_c} = {N \choose {N_1 \dots N_C}} \prod_{c=1}^C \theta_c^{N_c}$

where $\theta_c$ is the probability that the side $c$ shows up, and

$\displaystyle {N \choose {N_1 \dots N_C}} = \dfrac{N!}{N_1!N_2! \cdots N_C!}$

is the **mutlinomial coefficient**, which is the number of ways to divide a set of size $N = \sum_{c=1}^C N_c$ into subsets with sizes $N_1$ up to $N_C$. If $N=1$, the multinomial distribution becomes the categorical distribution.

Example: 
- $C=3$ categories: Apple, Banana, Cherry. 
- Probabilities: 
	- $\theta_1 = 0.5$ (Apple)
	- $\theta_2 = 0.3$ (Banana)
	- $\theta_3 = 0.2$ (Cherry)
- Total trials: $N=5$
- We observe the outcome counts: $y = (2,2,1) -$ 2 apples, 2 bananas, 1 cherry
- Compute Multinomial Probability:
	$\mathcal{M}(y | N = 5, \theta = [0.5, 0.3, 0.2]) = \dfrac{5!}{2!\cdot 2! \cdot 1!} \times 0.5^2 \times 0.3^2 \times 0.2^1 = 0.135$
## 2.5.2 Softmax function

In the conditional case, we can define

$p(y|x,\theta) = \text{Cat}(y|f(x;\theta))$

which we can also write as

$p(y|x,\theta) = \mathcal{M}(y|1,f(x;\theta))$

We require that $0 \le f_c(x;\theta) \le 1$ and $\sum_{c=1}^C f_c(x;\theta) = 1$ 

To avoid the requirement that $f$ directly predict a probability vector, it is common to pass the output from $f$ into the **softmax** function, also called the **multinomial logit**. This is defined as follows:

$\text{softmax}(a) = \displaystyle \left[\dfrac{e^{a_1}}{\sum_{c'=1}^C e^{a_{c'}}},\cdots,\dfrac{e^{a_C}}{\sum_{c'=1}^C e^{a_{c'}}}\right]$

This maps $\mathbb{R}^C$ to $[0,1]^C$, and satisfies the constraints that $0 \le \text{softmax}(a)_c \le 1$ and $\sum_{c=1}^C \text{softmax}(a)_c = 1$. The inputs to the softmax, $a = f(x;\theta)$, are called **logits**, and are a generalization of the log odds.

The softmax function is so-called since it acts a bit like the argmax function. To see this, let us divide each $a_c$ by a constant $T$ called the **temperature**. Then as $T \to 0$, we find

$\text{softmax}(a/T)_c = \begin{cases} 1.0 & \text{if } c = \arg\max_c' a_{c'} \\ 0.0 & \text{otherwise} \end{cases}$

In other words, at low temperatures, the distribution puts most of its probability mass in the most probable state (this is called **winner takes all**), whereas at high temperatures, it spreads the mass uniformly. See figure for an illustration.

![[Pasted image 20250725182526.png]]

## 2.5.3 Multiclass logistic regression

If we use a linear predictor of the form $f(x;\theta) = Wx + b$, where $W$ is a $C \times D$ matrix, and $b$ is a $C$-dimensional bias vector, the final model becomes

$p(y|x;\theta) = \text{Cat}(y|\text{softmax}(Wx + b))$

Let $a = Wx + b$ be the $C$-dimensional vector of **logits**. Then we can rewrite the above as follows:

$p(y=c|x;\theta) = \dfrac{e^{a_c}}{\sum_{c'=1}^C e^{a_{c'}}}$

This is known as **multinomial logistic regression**.

If we have just two classes, this reduces to binary logistic regression. To see this, note that

$\text{softmax}(a)_0 = \dfrac{e^{a_0}}{e^{a_0} + e^{a_1}} = \dfrac{1}{1 + e^{a_1 - a_0}} = \sigma(a_0 - a_1)$

so we can just train the model to predict $a = a_1 - a_0$. This can be done with a single weight vector $w$; if we use the multi-class formulation, we will have two weight vectors, $w_0$ and $w_1$. Such a model is **over-parameterized**, which can hurt interpretability, but the predictions will be the same.

Example in figure below shows what happens when we fit this model to the 3-class iris dataset, using just 2 features. We see that the decision boundaries between each class are linear. We can create nonlinear boundaries by transforming the features (e.g., using polynomials).

![[Pasted image 20250725184244.png]]

## 2.5.4 Log-sum-exp trick

We discuss one important practical detail to pay attention to when working with the softmax distribution. Suppose we want to compute the normalized probability $p_c = p(y=c|x)$, which is given by

$p_c = \dfrac{e^{a_c}}{Z(a)} = \dfrac{e^{a_c}}{\sum_{c'=1}^C e^{a_{c'}}}$

where $a = f(x;\theta)$ are the logits. We might encounter numerical problems when computing the **partition function** $Z$.

For example, suppose we have 3 classes, with logits $a = (0,1,0)$. Then we find $Z = e^0 + e^1 + e^0 = 4.71$. But now suppose $a = (1000, 1001, 1000)$; we find $Z = \infty$, since on a computer, even using 64 bit precision, `np.exp(1000)=inf`. Similarly, suppose $a = (-1000, -999, -1000)$; now we find $Z = 0$, since `np.exp(-1000)=0`. To avoid numerical problems, we can use the following identity:

$\displaystyle \log\sum_{c=1}^C \exp(a_c) = m + \log\sum_{c=1}^C \exp(a_c - m)$

This holds for any $m$. It is common to use $m = \max_c a_c$ which ensures that the largest value you exponentiate will be zero, so you will be zero, so you will definitely not overflow, and even if you underflow, the answer will be sensible. This is known as the **log-sum-exp trick**. We use this trick when implementing the **lse** function:

$\displaystyle \text{lse}(a) = \log \sum_{c=1}^C \exp(a_c)$

We can use this to compute the probabilities from the logits:

$p(y=c|x) = \exp(a_c - \text{lse}(a))$

We can then pass this to the cross-entropy loss.

However, to save computational effort and for numerical stability, it is quite common to modify the cross-entropy loss so that it takes logits $a$ as inputs, instead of the probability vector $p$. For example, consider the binary case. The $\text{CE}$ loss for one example is

$\displaystyle \mathcal{L} = -[\mathbb{I}(y=0)\log p_0 + \mathbb{I}(y=1) \log p_1]$

where

$\log p_1 = \log \left( \dfrac{1}{1 + \text{exp}(-a)} \right) = \log(1) - \log(1 + \exp(-a)) = 0 - \text{lse}([0,-a])$

$\log p_0 = 0 - \text{lse}([0, +a])$

# 2.6 Univariate Gaussian (normal) distribution

The most widely used distribution of real-valued random variables $y \in \mathbb{R}$ is the **Gaussian distribution**, also called the **normal distribution**.

## 2.6.1 Cumulative distribution function

We define the **cumulative distribution function** or **cdf** of a continuous random variable $Y$ as follows: 

$P(y) = \Pr(Y \le y)$

(Note that we use a capital $P$ to represent the cdf.) Using this, we can compute the probability of being in any interval as follows:

$\Pr(a \lt Y \le b) = P(b) - P(a)$

Cdf's are monotonically non-decreasing functions.

The cdf of the Gaussian is defined by

$\displaystyle \Phi(y;\mu,\sigma^2) = \int_{-\infty}^y \mathcal{N}(z|\mu,\sigma^2)dz$

See Figure(a) for the plot. Note that the cdf of the Gaussian is often implemented using $\Phi(y;\mu,\sigma^2) = \frac{1}{2}[1 + \text{erf}(z/\sqrt{2})]$, where $z = (y - \mu)/\sigma$ and $\text{erf}(\mu)$ is the **error function**, defined as

$\displaystyle\text{erf}(u) = \dfrac{2}{\sqrt{\pi}}\int_0^u e^{-t^2} dt$

![image.png](image%201.png)

The parameter $\mu$ encodes the mean of the distribution; in the case of a Gaussian, this is also the same as the mode. The parameter $\sigma^2$ encodes the variance. (Sometimes we talk about the **precision** of a Gaussian, which is the inverse variance, denoted $\lambda = 1/\sigma^2$.) When $\mu = 0$ and $\sigma = 1$, the Gaussian is called the **standard normal** distribution.

If $P$ is the cdf of $Y$, then $P^{-1}(q)$ is the value $y_q$ such that $p(Y \le y_q) = q$; this is called the $q$'th **quantile** of $P$. The value $P^{-1}(0.5)$ is the median of the distribution, with half of the probability mass on the left, and half on the right. The values $P^{-1}(0.25)$ and $P^{-1}(0.75)$ are the lower and upper **quartiles**.

For example, let $\Phi$ be the cdf of the Gaussian distribution $\mathcal{N}(0,1)$, and $\Phi^{-1}$ be the inverse cdf (also known as the **probit function**). Then points to the left of $\Phi^{-1}(\alpha/2)$ contain $\alpha/2$ of the probability mass, as illustrated in figure(b) below. By symmetry, points to the right of $\Phi^{-1}(1 - \alpha/2)$ also contain $\alpha/2$ of the mass. Hence the central interval $(\Phi^{-1}(\alpha/2), \Phi^{-1}(1 - \alpha/2))$ contains $1-\alpha$ of the mass. If we set $\alpha = 0.05$, the central $95\%$ is covered by the range

$(\Phi^{-1}(0.025), \Phi{-1}(0.975)) = (-1.96, 1.96)$

If the distribution is $\mathcal{N}(\mu, \sigma^2)$, then the $95\%$ interval becomes $(\mu - 1.96\sigma, \mu + 1.96\sigma)$. This is often approximated by writing $\mu \pm 2\sigma$.

![image.png](image%201.png)

## 2.6.2 Probability density function

We define the **probability density function** or **pdf** as the derivative of the cdf:

$p(y) = \dfrac{d}{dy} P(y)$

The pdf of the Gaussian is given by

$\mathcal{N}(y|\mu, \sigma^2) = \dfrac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{1}{2\sigma^2}(y - \mu)^2}$

where $\sqrt{2\pi\sigma^2}$ is the normalization constant needed to ensure the density integrates to 1. See figure(b) for plot

![image.png](image%201.png)

Given a pdf, we can compute the probability of a continuous variable being in a finite interval as follows:

$\displaystyle \Pr(a \lt Y \le b) = \int_a^b p(y)dy = P(b) - P(a)$

As the size of the interval gets smaller, we can write

$\Pr(y \le Y \le y+dy) \approx p(y)dy$

Intuitively, this says the probability of $Y$ being in a small interval around $y$ is the density at $y$ times the width of the interval. One important consequence of the above result is that the pdf at a point can be larger than 1. For example, $\mathcal{N}(0|0,0.1) = 3.99$.

We can use the pdf to compute the **mean**, or **expected** **value**, of the distribution:

$\displaystyle \mathbb{E}[Y] = \int_{\mathcal{Y}} yp(y)dy$

For a Gaussian, we have the familiar result that $\mathbb{E}[\mathcal{N}(\cdot|\mu,\sigma^2)] = \mu$. (Note, however, that for some distributions, this integral is not finite, so the mean is not defined.)

We can also use the pdf to compute the **variance** of a distribution. This is a measure of the "spread". and is often denoted by $\sigma^2$. The variance is defined as follows:

$\displaystyle \mathbb{V}[Y] = \mathbb{E}[(Y - \mu)^2] = \int(y-\mu)^2p(y)dy$
$\displaystyle \hspace{1cm} = \int y^2p(y)dy + \mu^2 \int p(y)dy - 2\mu \int yp(y)dy = \mathbb{E}[Y^2] - \mu^2$

from which we derive the useful result

$\mathbb{E}[Y^2] = \sigma^2 + \mu^2$

The **standard** **deviation** is defined as

$\text{std}[Y] = \sqrt{\mathbb{V}[Y]} = \sigma$

(This standard deviation can be more interpretable than the variance since it has same units as $Y$ itself.) For a Gaussian, we have the familiar result that $\text{std}\left[ \mathcal{N}(\cdot|\mu,\sigma^2) \right] = \sigma$.

## 2.6.3 Regression

So far we have been considering the unconditional Gaussian distribution. In some cases, it is helpful to make the parameters of the Gaussian be functions of some input variables, i.e., we want to create a conditional density model of the form

$\displaystyle p(y|x;\theta) = \mathcal{N}(y|f_{\mu}(x;\theta), f_{\sigma}(x;\theta)^2)$

where $f_{\mu}(x;\theta) \in \mathbb{R}$ predicts the mean, and $f_{\sigma}(x;\theta)^2 \in \mathbb{R}_+$ predicts the variance.

It is common to assume that the variance is fixed, and is independent of the input. This is called **homoscedastic regression**. Furthermore it is common to assume the mean is a linear function of the input. The resulting model is called **linear regression**:

$p(y|x;\theta) = \mathcal{N}(y|w^{\top}x + b, \sigma^2)$

where $\theta = (w,b,\sigma^2)$. See figure(a) for an illustration of this model in 1d.

![[Pasted image 20250725203202.png]]

However, we can also make the variance depend on the input; this is called **heteroskedastic regression**. In the linear regression setting, we have

$p(y|x;\theta) = \mathcal{N}(y|w_{\mu}^{\top}x + b, \sigma_+(w_{\sigma}^{\top}x))$

where $\theta = (w_{\mu}, w_{\sigma})$ are the two forms of regression weights, and 

$\sigma_+(a) = \log(1 + e^a)$

is the **softplus** function, that maps from $\mathbb{R}$ to $\mathbb{R}_+$, to ensure the predicted standard deviation is non negative. See figure(b) for an illustration of this model in 1d.

![[Pasted image 20250725203202.png]]

Note that figure plots the $95\%$ predictive interval, $[\mu(x) - 2\sigma(x), \mu(x) + 2\sigma(x)]$. This is the uncertainty in the predicted observation $y$ given $x$, and captures the variability in the blue dots. By contrast, the uncertainty in the underlying (noise-free) function is represented by $\sqrt{\mathbb{V}[f_{\mu}(x;\theta)]}$, which does not involve the $\sigma$ term; now the uncertainty is over the parameters $\theta$, rather than the output $y$.

## 2.6.4 Why is the Gaussian distribution so widely used?

First, it has two parameters which are easy to interpret, and which capture some of the most basic properties of a distribution, namely its mean and variance.
Second, the central limit theorem tells use that sums of independent random variables have an approximately Gaussian distribution, making it a good choice for modeling residual errors or "noise". 
Third, the Gaussian distribution makes the least number of assumptions (has maximum entropy), subject to the constraint of having a specified mean and variance; this makes it a good default choice in many cases.
Finally, it has a simple mathematical form, which results in easy to implement, but often highly effective, methods.

## 2.6.5 Dirac delta function as a limiting case

As the variance of a Gaussian goes to 0, the distribution approaches an infinitely narrow, but infinitely tall "spike" at the mean. We can write this as follows:

$\displaystyle \lim_{\sigma \to 0} \mathcal{N}(y|\mu, \sigma^2) \to \delta(y-\mu)$

where $\delta$ is the **Dirac delta function**, defined by

$\delta(x) = \begin{cases} +\infty & \text{if } x=0 \\ 0 & \text{if } x \ne 0 \end{cases}$

where

$\displaystyle \int_{-\infty}^{\infty} \delta(x)dx=1$

A slight variant of this is to define

$\delta_y(x) = \begin{cases} +\infty & \text{if } x = y \\ 0 & \text{if } x \ne y \end{cases}$

Note that we have

$\delta_y(x) = \delta(x-y)$

The delta function distribution satisfies the following **sifting property**, which we will use later on:

$\displaystyle \int_{-\infty}^{\infty} f(y)\delta(x-y)dy = f(x)$

# 2.7 Some other common univariate distributions *
We briefly introduce some other univariate distributions

## 2.7.1 Student $t$ distribution

The Gaussian distribution is quite sensitive to **outliers**. A **robust** alternative to the Gaussian is the **Student $t$-distribution**, which we shall call the **Student distribution** for short. Its pdf is as follows:

$\mathcal{T}(y|\mu,\sigma^2,\nu) \propto \left[ 1 + \dfrac{1}{\nu} \left( \dfrac{y-\mu}{\sigma} \right)^2 \right]^{-\left(\dfrac{\nu+1}{2}\right)}$

where $\mu$ is the mean, $\sigma \gt 0$ is the scale parameter (not the standard deviation), and $\nu \gt 0$ is called the **degrees of freedom** (although a better term would be the **degree of normality**, since large values of $\nu$ make the distribution act like a Gaussian).

We see that the probability density decays as a polynomial function of the squared distance from the center, as opposed to an exponential function, so there is more probability mass in the tail than with a Gaussian distribution, as shown in figure below. We say that the Student distribution has **heavy tails**, which makes it robust to outliers.

![[Pasted image 20250726120521.png]]

To illustrate the robustness of the Student distribution, consider Figure below. On the left, we show a Gaussian distribution and a Student distribution fit to some data with no outliers. On the right, we add some outliers. We see that the Gaussian is affected a lot, whereas the Student hardly changes. We discuss how to use the Student distribution for robust linear regression in Section 11.6.2.

![[Pasted image 20250726120845.png]]

For later reference, we note that the Student distribution has the following properties:

mean = $\mu$ , mode = $\mu$ , var = $\dfrac{\nu\sigma^2}{(\nu-2)}$

The mean is only defined if $\nu \gt 1$. The variance is only defined if $\nu \gt 2$. For $\nu \gg 5$, the Student distribution rapidly approaches a Gaussian distribution and loses its robustness properties. It is common to use $\nu=4$, which gives good performance in a range of problems.

## 2.7.2 Cauchy distribution

If $\nu=1$, the Student distribution is known as the **Cauchy** or **Lorentz** distribution. Its pdf is defined by

$\displaystyle \mathcal{C}(x|\mu,\gamma) = \dfrac{1}{\gamma\pi}\left[ 1 + \left( \dfrac{x-\mu}{\gamma} \right)^2 \right]^{-1}$

This distribution has very heavy tails compared to a Gaussian. For example, $95\%$ of the values from a standard normal are between $-1.96$ and $1.96$, but for a standard Cauchy they are between $-12.7$ and $12.7$. In fact the tails are so heavy that the integral that defines the mean does not converge.

The **half Cauchy** distribution is a version of the Cauchy (with $\mu = 0$) that is "folded over" on itself, so all its probability density is on the positive reals. Thus it has the form

$\displaystyle \mathcal{C}_+(x|\gamma) = \dfrac{2}{\pi\gamma} \left[ 1 + \left( \dfrac{x}{\gamma} \right)^2 \right]^{-1}$

This is useful in Bayesian modeling, where we want to use a distribution over positive reals with heavy tails, but finite density at the origin.

## 2.7.3 Laplace distribution

Another distribution with heavy tails is the **Laplace distribution**, also known as the **double sided exponential** distribution. This has the following pdf:

$\text{Laplace}(y|\mu,b) = \dfrac{1}{2b}\exp \left( - \dfrac{|y-\mu|}{b} \right)$

See figure below for a plot. Here $\mu$ is a location parameter and $b \gt 0$ is  a scale parameter. This distribution has the following properties:

mean = $\mu$ , mode = $\mu$ , var = $2b^2$

![[Pasted image 20250726120521.png]]

In section 11.6.1, we discuss how to use the Laplace distribution for robust linear regression, and in Section 11.4, we discuss how to use the Laplace distribution for sparse linear regression.

## 2.7.4 Beta distribution

The **beta distribution** has support over the interval $[0,1]$ and is defined as follows:

$\text{Beta}(x|a,b) = \dfrac{1}{B(a,b)}x^{a-1}(1-x)^{b-1}$

where $B(a,b)$ is the **beta function**, defined by

$B(a,b) = \dfrac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}$

where $\Gamma(a)$ is the Gamma function defined by

$\Gamma(a) = \int_0^\infty x^{a-1}e|^{-x}dx$

See Figure(a) below for plots of some beta distributions.

![[Pasted image 20250726124134.png]]
We require $a,b \gt 0$ to ensure the distribution is integrable (i.e., to ensure  $B(a,b)$ exists). If $a=b=1$, we get the uniform distribution. If $a$ and $b$ are both less than $1$, we get a binomial distribution with "spikes" at $0$ and $1$; if $a$ and $b$ are both greater than $1$, the distribution is unimodal. 

For later reference, we note that the distribution has the following properties

mean = $\dfrac{a}{a+b}$ , mode = $\dfrac{a-1}{a+b-2}$ , var = $\dfrac{ab}{(a+b)^2(a+b+1)}$

## 2.7.5 Gamma distribution

The **gamma distribution** is a flexible distribution for positive real valued rv's, $x \gt 0$. It is defined in two parameters, called the shape $a \gt 0$ and the rate $b \gt 0$:

$\text{Ga}(x|\text{shape}=a,\text{rate}=b) = \dfrac{b^a}{\Gamma(a)}x^{a-1}e^{-xb}$

Sometimes the distribution is parameterized in terms of the shape $a$ and the **scale** $s = 1/b$:

$\text{Ga}(x|\text{shape}=a,\text{scale}=s) = \dfrac{1}{s^a \Gamma(a)}x^{a-1}e^{-x/s}$

See figure(b) below for some plots of the gamma pdf.

![[Pasted image 20250726124134.png]]

For reference, we note that the distribution has the following properties:

mean = $\dfrac{a}{b}$ , mode = $\dfrac{a-1}{b}$ , var = $\dfrac{a}{b^2}$

There are several distributions which are just special cases of the Gamma, which we discuss below.

- **Exponential distribution**. This is defined by

	$\text{Expon}(x|\lambda) = \text{Ga}(x|\text{shape} = 1, \text{rate} = \lambda)$

	This distribution describes the times between events in a Poisson process, i.e. a process in which events occur continuously and independently at a constant average rate $\lambda$.

- **Chi-squared distribution**. This is defined by

	$\displaystyle \chi_{\nu}^2(x) = \text{Ga}\left(x|\text{shape} = \dfrac{\nu}{2}, \text{rate} = \dfrac{1}{2}\right)$

	where $\nu$ is called the degrees of freedom. This is the distribution of the sum of squared Gaussian random variables. More precisely, if $Z_i \sim \mathcal{N}(0,1)$, and $S = \sum_{i=1}^\nu Z_i^2$, then $S \sim \chi_\nu^2$.

- The **inverse Gamma distribution** is defined as follows:

	$\text{IG}(x|\text{shape} = a, \text{scale} = b) = \dfrac{b^a}{\Gamma(a)} x^{-(a+1)}e^{-b/x}$

	The distribution has these properties

	mean = $\dfrac{b}{a-1}$ , mode = $\dfrac{b}{a + 1}$ , var = $\dfrac{b^2}{(a-1)^2(a-2)}$

	The mean only exists if $a \gt 1$. The variance only exists if $a \gt 2$. Note: if $X \sim \text{Ga}(\text{shape} = a, \text{rate} = b)$, then $1/X \sim \text{IG}(\text{shape} = a, \text{scale} = b)$. (Note that $b$ plays two different roles in this case.)

## 2.7.6 Empirical distribution

Suppose we have a set of $N$ samples $\mathcal{D} = \{ x^{(1)}, \dots, x^{(N)} \}$, derived from a distribution $p(X)$, where $X \in \mathbb{R}$. We can approximate the pdf using a set of delta functions or "spikes", centered on these samples:

$\displaystyle \hat{p}_N(x) = \dfrac{1}{N} \sum_{n=1}^N \delta_{x^{(n)}}(x)$

This is called the **empirical distribution** of the dataset $\mathcal{D}$. An example of this, with $N=5$, is shown in Figure(a) below.

![[Pasted image 20250726132748.png]]

The corresponding cdf is given by

$\displaystyle \hat{P}_N(x) = \dfrac{1}{N} \sum_{n=1}^N \mathbb{I}\left( x^{(n)} \le x \right) = \dfrac{1}{N} \sum_{n=1}^N u_{x^{(n)}}(x)$

where $u_y(x)$ is a **step function** at $y$ defined by

$u_y(x) = \begin{cases} 1 & \text{if } x \ge y \\ 0 & \text{if } x \lt y \end{cases}$

This can be visualized as a "stair case", as in Figure(b) below, where the jumps of height $1/N$ occur at every sample.

![[Pasted image 20250726132748.png]]

# 2.8 Transformations of random variables

Suppose $x \sim p()$ is some random variable, and $y = f(x)$ is some deterministic transformation of it. In this section, we discuss how to compute $p(y)$.

## 2.8.1 Discrete case

If $X$ is a discrete rv, we can derive the pmf for $Y$ by simply summing up the probability mass for all the $x$'s such that $f(x) = y$:

$\displaystyle p_y(y) = \sum_{x:f(x)=y} p_x(x)$

For example, if $f(X) = 1$ if $X$ is even and $f(X) = 0$ otherwise, and $p_x(X)$ is uniform on the set $\{1,\dots,10\}$, then $p_y(1) = \sum_{x \in \{2,4,6,8,10\}}p_x(x)=0.5$, and hence $p_y(0)=0.5$ also. Note that in this example, $f$ is many-to-one function.

## 2.8.2 Continuous case

If $X$ is continuous, we cannot use previous equation since $p_x(x)$ is a density, not a pmf, and we cannot sum up densities. Instead, we work with cdf's, as follows:

$P_y(y) = \Pr(Y \le y) = \Pr(f(X) \le y) = \Pr\left(X \in \{x|f(x) \le y\}\right)$

If $f$ is invertible, we can use derive the pdf of $y$ by differentiating the cdf, as we show below. If $f$ is not invertible, we can use numerical integration, or a Monte Carlo approximation.

## 2.8.3 Invertible transformations (bijections)

In this section, we consider the case of monotonic and hence invertible functions. (Note a function is invertible iff it is a **bijector**). With this assumption, there is a simple formula for the pdf of $y$, as we will see. (This can be generalized to invertible, but non-monotonic, functions, but we ignore this case.)

### 2.8.3.1 Change of variables: scalar case

We start with an example. Suppose $x \sim \text{Unif}(0,1)$, and $y=f(x)=2x+1$. This function stretches and shifts the probability distribution, as shown in figure(a) below.

![[Pasted image 20250726135700.png]]

Now let us zoom in on a point $x$ and another point that is infinitesimally close, namely $x + dx$. We see this interval gets mapped to $(y,y+dy)$. The probability mass in these intervals must be the same, hence $p(x)dx = p(y)dy$, and so $p(y) = p(x)dx/dy$. However, since it does not matter (in terms of probability preservation) whether $dx/dy \gt 0$ or $dx/dy \lt 0$, we get

$p_y(y) = p_x(x)\left|\dfrac{dx}{dy}\right|$

Now consider the general case for any $p_x(x)$ and any monotonic function $f:\mathbb{R} \to \mathbb{R}$. Let $g = f^{-1}$, so $y = f(x)$ and $x = g(y)$. If we assume that $f: \mathbb{R} \to \mathbb{R}$ is monotonically increasing we get

$P_y(y) = \Pr(f(X) \le y) = \Pr(X \le f^{-1}(y)) = P_x(f^{-1}(y)) = P_x(g(y))$

Taking derivatives we get

$p_y(y) = \dfrac{d}{dy} P_y(y) = \dfrac{d}{dy} P_x(x) = \dfrac{dx}{dy}\dfrac{d}{dx} P_x(x) = \dfrac{dx}{dy}p_x(x)$

We can derive a similar expression (but with opposite signs) for the case where $f$ is monotonically decreasing. To handle the general case we take the absolute value to get

$p_y(y) = p_x(g(y))\left|\dfrac{d}{dy}g(y)\right|$

This is called **change of variables** formula.

### 2.8.3.2 Change of variables: multivariate case

We can extend the previous results to multivariate distributions as follows. Let $f$ be an invertible function that maps $\mathbb{R}^n$ to $\mathbb{R}^n$, with inverse $g$. Suppose we want to compute the pdf of $y = f(x)$. By analogy with the scalar case, we have

$p_y(y) = p_x(g(y))|\det[\mathbf{J}_g(y)]|$

where $\mathbf{J}_g=\dfrac{dg(y)}{dy^{\top}}$ is the Jacobian of $g$, and $|\det \mathbf{J}(y)|$ is the absolute value of the determinant of $\mathbf{J}$ evaluated at $y$.

Figure illustrates this result in 2d, for the case where $f(x) = Ax + b$, where $\mathbf{A} = \begin{pmatrix} a & c \\ b & d \end{pmatrix}$.
![[Pasted image 20250728181625.png]]
We see that the area of the unit square changes by a factor of $\det(A) = ad - bc$, which is the area of the parallelogram.
As another example, consider transforming a density from Cartesian coordinates $x = (x_1,x_2)$ to polar coordinates $y = f(x_1, x_2)$, so $g(r,\theta) = (r\cos \theta, r \sin \theta)$. Then

$\displaystyle \mathbf{J}_g = \begin{pmatrix}\frac{\partial x_1}{\partial r} & \frac{\partial x_1}{\partial\theta} \\[1pt]\frac{\partial x_2}{\partial r} & \frac{\partial x_2}{\partial \theta}\end{pmatrix}=\begin{pmatrix}\cos\theta & -r\sin\theta \\\sin\theta & r\cos\theta\end{pmatrix}$

$|det(J_g)| = |r\cos^2 \theta + r\sin^2 \theta| = |r|$

Hence

$p_{r,\theta}(r,\theta) = p_{x1,x2}(r\cos \theta, r \sin \theta)r$

To see this geometrically, notice that the area of the shaded patch in Figure below is given by 

$\Pr(r \le R \le r + dr, \theta \le \Theta \le \theta + d\theta) = p_{r,\theta}(r,\theta)drd\theta$

![[Pasted image 20250808123904.png]]

In the limit, this is equal to the density at the center of the patch times the size of the patch, which is given by $r$ $dr$ $d\theta$. Hence

$p_{r,\theta}(r,\theta)\hspace{1mm}dr\hspace{1mm}d\theta = p_{x1,x2}(r\cos \theta, r\sin \theta)\hspace{1mm}r\hspace{1mm}dr\hspace{1mm}d\theta$

## Moments of a linear transformation

Suppose $f$ is an affine function, so $y = \mathbf{A}x + b$. In this case, we can easily derive the mean and covariance of $y$ as follows. First, for the mean, we have

$\mathbb{E}[y] = \mathbb{E}[\mathbf{A}x + b] = \mathbf{A}\mu + b$

where $\mu = \mathbb{E}[x]$. If $f$ is a scalar-valued function, $f(x) = a^{\top}x + b$, the corresponding result is 

$\mathbb{E}[a^{\top}x + b] = a^{\top}\mu + b$

For the covariance, we have

$\text{Cov}[y] = \text{Cov}[\mathbf{A}x + b] = \mathbf{A}\sum \mathbf{A}^{\top}$

where $\sum = \text{Cov}[x]$. We leave the proof of this as an exercise.

As a special case, if $y = a^{\top}x + b$, we get

$\mathbb{V}[y] = \mathbb{V}[a^{\top}x + b] = a^{\top}x + b$

For example compute the variance of the sum of two scalar random variables, we can set $a = [1,1]$ to get

$\mathbb{V}[x_1 + x_2] = \begin{pmatrix} 1 & 1 \end{pmatrix} \begin{pmatrix} \sum_{11} & \sum_{12} \\ \sum_{21} & \sum_{22} \end{pmatrix} \begin{pmatrix} 1 \\ 1 \end{pmatrix}$

Note, however, that although some distributions (such as the Gaussian) are completely characterized by their mean and covariance, in general we must use the techniques described above to derive the full distribution of $y$.

## 2.8.5 The convolution theorem

Let $y = x_1 + x_2$, where $x_1$ and $x_2$ are independent rv's. If these are disrete random variables, we can compute the pmf for the sum as follows:

$p(y = j) = \sum_{k}p(x_1 = k)p(x_2 = j - k)$

for $j = \dots, -2, -1, 0,1,2,\dots$

If $x_1$ and $x_2$ have pdf's $p_1(x_1)$ and $p_2(x_2)$, what is the distribution of $y$? The cdf for $y$ is given by

$\displaystyle P_y(y^*) = \Pr(y \le y^*) = \int_{-\infty}^{\infty} p_1(x_1)\left[\int_{-\infty}^{y^* - x_1} p_2(x_2)dx_2\right]dx_1$

where we integrate over the region $R$ defined by $x_1 + x_2 \lt y^*$. Thus the pdf for $y$ is

$\displaystyle p(y) = \left[ \dfrac{d}{dy^*} P_y(y^*) \right]_{y^*=y} = \int p_1(x_1)p_2(y-x_1)dx_1$ ------------> $(2.170)$

where we used the rule of **differentiating under the integral sign**:

$\displaystyle \dfrac{d}{dx} \int_{a(x)}^{b(x)} f(t)dt = f(b(x)) \dfrac{db(x)}{dx} - f(a(x)) \dfrac{da(x)}{dx}$

We can write equation $2.170$ as follows:

$p = p_1 \circledast p_2$

where $\circledast$ represents the **convolution** operator. For finite length vectors, the integrals become sums, and convolution can be thought of as a "flip and drag" operation, as illustrated in Table below. Consequently, Equation $(2.170)$ is called the **convolution theorem**

For example, suppose we roll two dice, so $p_1$ and $p_2$ are both the discrete uniform distributions over $\{ 1,2,\dots,6 \}$. Let $y  = x_1 + x_2$ be the sum of the dice. We have

$p(y=2) = p(x_1=1)p(x_2=1) = \dfrac{1}{6}\dfrac{1}{6} = \dfrac{1}{36}$

$p(y=3) = p(x_1=1)p(x_2=2)+p(x_1=2)p(x_2=1)=\dfrac{1}{6}\dfrac{1}{6} + \dfrac{1}{6}\dfrac{1}{6} = \dfrac{2}{36}$

$\hspace{2cm}\dots$
Continuing in this way



