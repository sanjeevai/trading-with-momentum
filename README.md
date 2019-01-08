
# Artificial Intelligence for Trading Nanodegree

## Momentum Trading

## Project: Trading with Momentum

## Table of Contents

1. [Project Overview](#overview)
2. [Data](#data)
3. [Trading Signal](#signal)
4. [Trading Strategy](#strategy)
5. [Performace of Portfolio](#performance)
6. [Statistical Tests](#tests)
    1. [Annualized Rate of Return](#annualized_ret)
    2. [T-Test](#t_test)
7. [Conclusion](#conclusion)
8. [Files](#files)
9. [Libraries](#lib)

<a id='overview'></a>

***

### Project Overview

In this project, we will implement a momentum [**trading strategy**](#4), and test it to see if it has the potential to be **profitable**. We are supplied with a universe of stocks and time range. We are also provided with a textual description of how to generate a trading signal based on a [**momentum indicator**.](#m_indicator) We will then compute the signal for the time range given and apply it to the dataset to produce [**projected returns.**](#projected_ret) Finally, we will perform a statistical test on the mean of the returns to conclude if there is an **alpha** in the signal.

<a id='data'></a>

### Data

For the dataset, we will use the end of day from [Quotemedia](https://www.quotemedia.com/). This contains data for many stocks, but we will look at stocks in the **S&P 500.** We will also make things a little easier to run by narrowing down our range of time period instead of using all of the data.

Udacity doesn't have a license to redistribute the data to us. They are working on alternatives to this [problem](https://github.com/udacity/artificial-intelligence-for-trading/#no-data).

For all the examples, we will use **Apple's stock (AAPL)**. If we try to graph all the stocks, it would be too much information.

<a id='signal'></a>

### Trading Signal

The trading signal we'll develop in this project does not need to be based on daily prices, for instance, we can use **month-end prices** to perform trading once a month. To do this, we must first resample the **daily adjusted closing prices** into monthly buckets, and select the last observation of each month.

<a id='m_indicator'></a>

**Computed Log returns** from prices is our primary momentum indicator.

A **trading signal** is a sequence of trading actions, or results that can be used to take trading actions. A common form is to produce a "long" and "short" portfolio of stocks on each date (e.g. end of each month, or whatever frequency you desire to trade at). This signal can be interpreted as **rebalancing your portfolio** on each of those dates, entering long ("buy") and short ("sell") positions as indicated.

<a id='strategy'></a>

### Trading Strategy

Here's a strategy that we will try:

> For each month-end observation period, rank the stocks by previous returns, from the highest to the lowest. Select the top performing stocks for the long portfolio, and the bottom performing stocks for the short portfolio.

<a id='performance'></a>

### Performance of Portfolio

It's now time to check if our trading signal has the potential to become profitable!

We'll start by computing the net returns this portfolio would return. For simplicity, we'll assume every stock gets an equal dollar amount of investment. This makes it easier to compute a portfolio's returns as the simple arithmetic average of the individual stock returns.

<a id='projected_ret'></a>

 The `portfolio_returns` function to compute the **expected portfolio returns.** Using `df_long` to indicate which stocks to long and `df_short` to indicate which stocks to short, it calculates the returns using `lookahead_returns`. To help with calculation, `n_stocks` is the number of stocks we're investing in a single period.

```python
def portfolio_returns(df_long, df_short, lookahead_returns, n_stocks):
    """
    Compute expected returns for the portfolio, assuming equal
    investment in each long/short stock.

    Parameters
    ----------
    df_long : DataFrame
        Top stocks for each ticker and date marked with a 1
    df_short : DataFrame
        Bottom stocks for each ticker and date marked with a 1
    lookahead_returns : DataFrame
        Lookahead returns for each ticker and date
    n_stocks: int
        The number number of stocks chosen for each month

    Returns
    -------
    portfolio_returns : DataFrame
        Expected portfolio returns for each ticker and date
    """

    return ((df_long - df_short) * lookahead_returns)/n_stocks
```
<a id='tests'></a>

### Statistical Tests

<a id='annualized_ret'></a>

#### Annualized Rate of Return

The annualized rate of return allows you to compare the rate of return from this strategy to other quoted rates of return, which are usually quoted on an annual basis.

<a id='t_test'></a>

#### T-test

Our null hypothesis (H<sub>0</sub>) is that the actual mean return from the signal is zero. We'll perform a one-sample, one-sided t-test on the observed mean return, to see if we can reject H<sub>0</sub>.

For this project, we'll use alpha level = 0.05, since it's a common value to use.

The `analyze_alpha` function performs a t-test on the sample of portfolio returns.

<a id='conclusion'></a>

### Conclusion

T-test returned a **p-value of 0.21.** This is a very high p-value so we cannot reject the null hypothesis. We come to the conclusion from t-test that our signal was not strong enough to give us positive returns. In other words, our signal is **not profitable.**

<a id='files'></a>

### Files

- `helper` and `project_helper` module contain utility functions and graph functions.

- `project_tests` contains unit tests for all the problems

- `tests` is used to construct test cases for unit tests.

<a id='lib'></a>

### Libraries

These necessary libraries are mentioned in `requirements.txt`:

- [colour==0.1.5](https://github.com/vaab/colour)

Converts and manipulates common color representation (RGB, HSL, web, …)

- [cvxpy==1.0.3](https://github.com/cvxgrp/cvxpy/)

Modeling language for convex optimization problems. It allows you to express your problem in a natural way that follows the math, rather than in the restrictive standard form required by solvers.

- [cycler==0.10.0](https://matplotlib.org/cycler/)

Composable style cycles

- [numpy==1.13.3](http://www.numpy.org/)

NumPy is the fundamental package for scientific computing with Python.

- [pandas==0.21.1](https://github.com/pandas-dev/pandas)

Flexible and powerful data analysis / manipulation library for Python, providing labeled data structures similar to R `data.frame` objects, statistical functions, and much more.

- [plotly==2.2.3](https://plot.ly/python/)

Python plotting library for collaborative, interactive, publication-quality graphs.

- [pyparsing==2.2.0](https://github.com/pyparsing/pyparsing/)

The pyparsing module is an alternative approach to creating and executing simple grammars, vs. the traditional lex/yacc approach, or the use of regular expressions.

- [python-dateutil==2.6.1](https://dateutil.readthedocs.io/en/stable/)

Extensions to the standard Python datetime module.

- [pytz==2017.3](https://pythonhosted.org/pytz/)

This library allows accurate and cross platform timezone calculations using Python 2.4 or higher.

- [requests==2.18.4](http://docs.python-requests.org/en/master/)

Requests is an elegant and simple HTTP library for Python, built for human beings.

- [scipy==1.0.0](https://www.scipy.org/)

Python-based ecosystem of open-source software for mathematics, science, and engineering.

- [scikit-learn==0.19.1](https://scikit-learn.org/stable/)

A set of python modules for machine learning and data mining.

- [six==1.11.0](https://github.com/benjaminp/six)

Six is a Python 2 and 3 compatibility library. It provides utility functions for smoothing over the differences between the Python versions with the goal of writing Python code that is compatible on both Python versions.

- [tqdm==4.19.5](https://tqdm.github.io/)

A fast, extensible progress bar for Python and CLI