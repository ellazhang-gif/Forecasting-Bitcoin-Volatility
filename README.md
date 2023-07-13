# Abstract

Volatility is an indicator that describes the degree of dispersion of a
security's returns over time and it is used as a tool to measure risk,
playing an important role in the financial market such as derivatives
pricing, asset allocation, risk management and hedging. In our research,
we study the volatility of asset return series varying with time by
comparing two mainstream approaches: the general autoregressive
conditional heteroskedasticity (GARCH) model and its variants, and the
stochastic volatility (SV) model that is currently popular in the
western econometrics community. We will complete a relative accurate and
stable model and parameter estimation by applying algorithms such as
MCMC estimation, then compare their forecasting power based on certain
dataset and financial instrument. Being Aware of the strengths and
drawbacks of each model, we will also propose our improvement and
optimization for these models so that they can fully describe the
characteristics of volatility while maintaining their forecasting
ability.

# Research Question and Significance

Volatility makes the financial market difficult to predict. The two
mainstream approaches to study volatility are GARCH and SV models but
both of them have their own strengths and drawbacks. Therefore, we
wonder whether there is a way to combine these two models together if
that makes sense at all to solve the problems each of them has. In this
research, we would like to:

1\) Find appropriate parameters for both models.

2\) Compare and evaluate the forecasting effet of the two models based
on datasets (such as

::: CJK
UTF8gbsn上证
:::

50ETF, S&P 500). Models will be evaluated based on whether it is good at
capturing volatility characteristics of the stock market, such as
volatility aggregation, asymmetry, the leverage effect, etc. All aspects
will be considered to find the model with better (or best) overall
forecasting effect.

3\) We would also propose optimization for the model with relative poor
performance. Similarly, we will apply the improved model to real-world
data to measure the effect of our improvement.

Blending together both the models proposed in the latest financial
econometrics literature and our potential improvement, we will try our
best to come up with a model with 1) better performance in measuring and
forecasting the volatility of certain financial instruments; 2) more
accuracy and stability in parameter estimation; 3) specifically
applicable to certain financial instruments.

# Project Design and Feasibility

## Model

### ARCH Model

Engle proposed the Autoregressive Conditional Heteroskedasticity (ARCH)
model in 1982. The basic idea is that, for a time series, the occurrence
of a noise at a given moment under a previous information set obeys a
normal distribution that has zero mean, the variance is a time-varying
quantity (i.e., conditional heteroskedasticity), and this time-varying
variance is a linear combination of the squared noise values of a finite
number of terms in the past (i.e., it is autoregressive). This
constitutes the autoregressive conditional heteroskedasticity model:
$$a_t = \sigma_t \cdot \epsilon_t$$
$$\sigma^{2}_t = \alpha_0 + {\alpha_1}{a^{2}_{t-1}}+ \cdots + {\alpha_m}{a^{2}_{t-m}}$$

where $a_t = r_t - E(r_t \mid F_{t-1})$ with $r_t$ the logarithmic
return of the asset at time $t$ and $F_{t-1}$ the observation at time
$t-1$, is the perturbation of asset return series, {$\epsilon_t$} is an
i.i.d white noise series with zero mean and unit variance,
$\sigma^{2}_t$ denotes the conditional heteroscedasticity of $a_t$, and
$\alpha_i > 0$ for $i=0$ and $\alpha_i \geq 0$ for any $i \geq 1$.

### GARCH Model

Bollerslev proposed an important extension of the ARCH model in 1986,
called the GARCH model. Compared with ARCH models which require a large
number of parameters and complicated estimation procedures, GARCH models
require only three parameters. Thus its expression is more concise and
easier to estimate, the mathematical expressions of GARCH$(m, s)$ model
are as follows: $$a_t = \sigma_t \cdot \epsilon_t$$
$$\sigma^{2}_t = \alpha_0 + \sum_{i=1}^{m}{\alpha_i}{a^{2}_{t-i}} + \sum_{j=1}^{s}{\beta_j}{\sigma^{2}_{t-j}}$$

The notations are the same as before and here ${\beta_j} \geq 0$ for any
$j \geq 1$. These models have made significant contributions to the
modeling of time-varying volatility and the estimation of the
persistence of volatility. However, prediction results reveal some
drawbacks of ARCH and GARCH models. First, since the historical
observations of the time series affect volatility by their squares,
positive and negative perturbations will have the same effect, i.e., the
conditional variance responds symmetrically to positive and negative
price changes. However, it has been observed that larger negative
perturbations cause more volatility than positive ones, which is
asymmetrical. Moreover, many characteristics of volatility, such as
leverage effects, cannot be characterized by GARCH models. Also, the
conditional variance in this model is a deterministic function that does
not adequately capture the effect of stochastic factors on volatility.
Therefore, we further investigate the Stochastic Volatility (SV) model
that included the variance as an unobservable term.

### Stochastic Volatility (SV) Model

Another way to describe volatility is to use the SV model, where the
variance is an unobservable variable and a stochastic term is added to
reflect the effect of stochastic factors on volatility:
$$a_t = \epsilon_t \cdot e^{\frac{\sigma_t}{2}}$$
$$\sigma_t = \alpha + \beta \sigma_{t-1} + \eta_t$$

Where {$\epsilon_t$} and {$\eta_t$} are uncorrelated white noise series,
$\alpha$, $\beta$ are constants and other notations the same as before.
Note that since {$\eta_t$} is a stochastic term, $\sigma_t$ is
unobservable. In this way, the parameter estimation procedure will
become remarkably complicated. We are currently aware of several methods
for parameter estimation of SV models: maximum simulated likelihood
estimation, pseudo maximum likelihood estimation, generalized method of
moments (GMM), efficient method of moments (EMM), and Markov Chain Monte
Carlo (MCMC) estimation.

## Our Approach

1.  We will use several procedures available in econometrics to derive
    the formula for the estimation of parameters of both GARCH and SV
    models. Prime amongst these are listed in the previous section. We
    will mainly pay attention to frequency domain quasi maximum
    likelihood (FDQML), GMM, and MCMC estimation and if time permits, we
    will look through each method and figure out the most appropriate
    one (probably with our improvements).

2.  We use data of different estimation window and frequency to compare
    both models' forecast abilities based on stock prices. We will
    evaluate the models based on metrics such as R2, logVol R2,
    SqrtVolatility, MSE, etc. on datasets (such as

    ::: CJK
    UTF8gbsn上证
    :::

    50ETF, S&P 500).

3.  We will do simulation study with these two models and propose
    optimization and improvement for the model with relative poor
    performance. Similarly, we will apply the improved model to
    real-world data to measure the effect of our improvement.

# Background and group partnership plan

The three team members come from diverse academic background in Computer
Science, Mathematics, Business and Economics. Yimeng is proficient in
using Python and Minitab to analyze data. The Forecasting Time Series at
Stern prepares her with the statistical foundation of analyzing
time-series data such as stock index/returns with rigorous models.
Yuejia has taken stochastic processes and math of finance, which
equipped her knowledge of Brownian motion, random walks and martingales.
She is proficient in using Matlab to find numerical solutions to
complicated equations. Pinyi has taken advanced microeconomics and
advanced econometrics which enable her to construct a model and analyze
them. She is familiar with Stata and can use it to visualize and analyze
data.

Working as a team allows us to pool our ideas, letting one of us take
charge of one model of the project enables us to get greater depth in
this area. Moreover, the different knowledge that we gained from
different majors can equip us with specific skills to work on related
areas. In doing the research, we will split our total work equally so
that each group member will be in charge of a part of the research. This
guarantees the consistency of each part, avoiding frequent handover. We
will have meetings every week with our mentor to share our existing
problems and make sure everything is on track.

# Feedback and evaluation

Professor Dan Wang will be our mentor and provide us with feedback. We
will meet her every week to ensure that we are on the right track and
have everything under control. She will evaluate our work through
several parts including necessity, accuracy, and logic. Necessity is to
ensure the main track of our research, accuracy is the requirement on
the samples, estimation and analyzing method. Logic is the overall
control, connection and causality between models. Every part of the
research should be interlocked, and this is also the most important
thing for successful research.

# Dissemination of Knowledge

Our research would be presented in the form of the papers with the
statistical data revealed. We might also join the Undergraduate Research
Symposium or other academic conference to share our findings with
students and professors.
