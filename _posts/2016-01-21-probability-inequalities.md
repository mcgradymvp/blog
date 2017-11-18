---
title: "Probablity Inequalities"
tags:
- Tutorial
- Competitions
---
# Probability Inequalities
#### Markov's Inequality
Let $X$ be a non-negative random variable. For any $t>0$, $P(X>t)\leq \frac{E(X)}{t}$.

$Proof$. Since $X>0$,
$$
  \begin{align}
    E(X) &=\int_0^{\infty} xp(x)dx=\int_0^t xp(x)dx+\int_t^{\infty} xp(x)dx\\
    & \geq \int_t^{\infty} xp(x)dx \geq t\int_t^{\infty} p(x)dx=tP(X>t).
  \end{align}
$$

#### Chebyshev's Inequality
Let $\mu = E(X)$ and $\sigma^2=Var(X)$. Then,
$$
  P(|X-\mu|\geq t)\leq \frac{\sigma^2}{t^2}.
$$
$Proof$. By $Markov's$ $Inequality$,
$$
  P(|X-\mu|\geq t)=P(|X-\mu|^2 \geq t^2) \leq \frac{E[(X-\mu)^2]}{t^2}=\frac{\sigma^2}{t^2}.
$$

#### Hoeffding's Inequality
Let $Y_1, Y_2,\ldots, Y_n$ be independent random variables. $E(Y_i)=0$ and $a_i\leq Y_i \leq b_i$.
Let $\varepsilon>0$, then for any $t>0$,
$$
  P(\sum_{i=1}^n Y_i \geq \varepsilon) \leq e^{-t\varepsilon}\prod_{i=1}^n e^{t^2(b_i-a_i)^2/8}
$$
$Proof$. Consider that
$$
  \begin{align}
    P(\sum_{i=1}^n Y_i & \geq \varepsilon)=P(t\sum_{i=1}^n Y_i \geq t\varepsilon)\\
    & =P(e^{t\sum_{i=1}^n Y_i}\geq e^{t\varepsilon})\\
    & \leq e^{-t\varepsilon}E(e^{t\sum_{i=1}^n Y_i})\\
    & =e^{-t\varepsilon}\prod_{i=1}^nE(e^{tY_i})
  \end{align}
$$
Since $a_i\leq Y_i \leq b_i$, we can write $Y_i$ as $Y_i=\alpha b_i +(1-\alpha)a_i$ for some $\alpha\in[0,1]$.
So $\alpha = \frac{Y_i-a_i}{b_i-a_i}$.
We also noticed that $e^{ty}$ is a convex function, therefore,
$$
e^{tY_i}\leq\frac{Y_i-a_i}{b_i-a_i}e^{tb_i}+\frac{b_i-Y_i}{b_i-a_i}e^{ta_i}\\
\Rightarrow \qquad E(e^{tY_i})\leq -\frac{a_i}{b_i-a_i}e^{tb_i}+\frac{b_i}{b_i-a_i}e^{ta_i}
$$
If we take
$$
\begin{align}
& u=t(b_i-a_i)\\
& g(u)=-\gamma u+\log(1-\gamma+\gamma e^u)\\
& \gamma=-\frac{a_i}{b_i-a_i}
\end{align}
$$
Then we have
$$ E(e^{tY_i})\leq e^{g(u)} $$
By Taylor's Theorem,
$$
g(u)\leq g(0)+ug'(0)+\frac{u^2}{2}g''(0)\leq \frac{u^2}{8}=\frac{t^2(b_i-a_i)^2}{8}
$$
So
$$
  E(e^{tY_i})\leq e^{t^2(b_i-a_i)^2/8}\\
  \Rightarrow\qquad P(\sum_{i=1}^n Y_i \geq \varepsilon) \leq e^{-t\varepsilon}\prod_{i=1}^n e^{t^2(b_i-a_i)^2/8}
$$

#### Mill's Inequality
let $Z\sim N(0,1)$. Then,
$$
P(|Z|>t)\leq \sqrt{\frac{2}{\pi}}e^{-\frac{t^2}{2}}/t
$$
$Proof$.
$$
\begin{align}
  P(|Z|>t)=2P(Z>t) & =\frac{1}{\sqrt{2\pi}}\int_t^{infty} e^{-\frac{1}{2}x^2}dx\\
  &\leq\frac{1}{\sqrt{2\pi}}\int_t^{infty}\frac{x}{t}e^{-\frac{1}{2}x^2}dx\\
  &=\frac{1}{t\sqrt{2\pi}}\Big(-e^{-\frac{1}{2}x^2}|_t^{\infty}\Big)\\
  &=\frac{1}{t\sqrt{2\pi}}e^{-\frac{1}{2}t^2}
\end{align}
$$
Therefore,
$$P(|Z|>t)\leq \sqrt{\frac{2}{\pi}}e^{-\frac{t^2}{2}}/t.$$

#### Cauchy-Schwartz Inequality
If $X$ and $Y$ have finite variances, then
$$
E(XY)\leq\sqrt{E(X^2)E(Y^2)}
$$
$Proof$. Let's consider $E[(X-\alpha Y)^2]$.
$$
0\leq E[(X-\alpha Y)^2]=E(X^2)+\alpha^2 E(Y^2)-2\alpha E(XY)
$$
If we take $\alpha=\frac{E(XY)}{E(Y^2)}$
$$
0\leq E(X^2)-\frac{[E(XY)]^2}{E(Y^2)}
$$
which is
$$
E(XY)\leq\sqrt{E(X^2)E(Y^2)}.
$$

#### Jensen's Inequality
If $g(x)$ is convex, then $E(g(X))\geq g(E)$. If $g(x)$ is concave, then $E(g(X))\leq g(E)$.

$Proof$.
Let's take $L=a+bX$ as a tangent line to $g(x)$ at $E(X)$.

Since $g(x)$ is convex,
$$
E(g(X))\geq E(a+bX)=a+bE(X)=g(E(X)).
$$


We are now ready to split the test and training sets back into their original states, carrying our fancy new engineered variables with them. The nicest part of what we just did is how the factors are treated in R. Behind the scenes, factors are basically stored as integers, but masked with their text names for us to look at. If you create the above factors on the isolated test and train sets separately, there is no guarantee that both groups exist in both sets.

For instance, the family "3Johnson" previously discussed does not exist in the test set. We know that all three of them survive from the training set data. If we had built our factors in isolation, there would be no factor "3Johnson" for the test set. This would upset any machine learning model because the factors between the training set used to build the model and the test set it is asked to predict for are not consistent. ie. R will throw errors at you if you try.

Because we built the factors on a single dataframe, and then split it apart after we built them, R will give all factor levels to both new dataframes, even if the factor doesn't exist in one. It will still have the factor level, but no actual observations of it in the set. Neat trick right? Let me assure you that manually updating factor levels is a pain.

So let's break them apart and do some predictions on our new fancy engineered variables:

```r
> train <- combi[1:891,]
> test <- combi[892:1309,]
```

Here we introduce yet another subsetting method in R; there are many depending on how you want to chop up your data. We have isolated certain ranges of rows of the combi dataset based on the sizes of the original train and test sets. The comma after that with no numbers following it indicates that we want to take ALL columns with this subset and store it to the assigned dataframe. This gives us back our original number of rows, as well as all our new variables including the consistent factor levels.

Time to do our predictions! We have a bunch of new variables, so let's send them to a new decision tree. Last time the default complexity worked out pretty well, so let's just grow a tree with the vanilla controls and see what it can do:

```r
> fit <- rpart(Survived ~ Pclass + Sex + Age + SibSp + Parch + Fare + Embarked + Title + FamilySize + FamilyID,
data=train,
method="class")
```

![Engineered tree]({{ site.url }}/images/2014-01-16-r-part-4-feature-engineering-2.png){: .align-center}

Interestingly our new variables are basically governing our tree. Here's another drawback with decision trees that I didn't mention last time: they are biased to favour factors with many levels. Look at how our 61-level FamilyID factor is so prominent here, and the tree picked out all the families that are biased one way more than the others. This way the decision node can chop and change the data into the best way possible combination for purity of the following nodes.

But all that aside, you know should know how to create a submission from a decision tree, so let's see how it performed!

![Submission 6]({{ site.url }}/images/2014-01-16-r-part-4-feature-engineering-3.png){: .align-center}

Awesome, we just almost halved our rank! All by squeezing a bit more value out of what we already had. And this is just a sample of what you might be able to find in this dataset.

Go ahead and try and create some more engineered variables! As before, I also really encourage you to play around with the complexity parameters and maybe try trimming some deeper trees to see if it helps or hinders your rank. You may even consider excluding some variables from the tree to see if that changes anything too.

In most cases though, the title or gender variables will govern the first decision due to the greedy nature of decision trees. The bias towards many-levelled factors won't go away either, and the overfitting problem can be difficult to gauge without actually sending in submissions, but good judgement can help.

Next lesson, we will overcome these limitations by building an ensemble of decision trees with the powerful Random Forest algorithm. [Go there now!]({{ site.url }}/kaggle-titanic-tutorial/r-part-5-random-forests){:target="_blank"}

All code from this tutorial is available on my [Github repository](https://github.com/trevorstephens/titanic){:target="_blank"}

