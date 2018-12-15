
# Artificial Intelligence for Trading

## Momentum Trading

## Project: Trading with Momentum

## Table of Contents

1. [Project Overview](#1)
2. [Data](#2)
3. [Trading Strategy](#3)
4. [Performace of Portfolio](#4)
5. [Statistical Tests](#5)
    1. [Annualized Rate of Return](#5_1)
    2. [T-Test](#5_2)
6. [Conclusion](#6)
7. [Files](#7)
8. [Libraries](#8)

<a id='1'></a>

### Project Overview

In this project, I implemented a trading strategy on my own, and tested to see if it has the potential to be profitable. I was supplied with a universe of stocks and time range. I was also provided with a textual description of how to generate a trading signal based on a momentum indicator. I then computed the signal for the time range given and applied it to the dataset to produce projected returns. Finally, I performed a statistical test on the mean of the returns to conclude if there was alpha in the signal.

<a id='2'></a>
### Data

For the dataset, we used the end of day from Quotemedia. This contains data for many stocks, but we looked at stocks in the S&P 500. We also made things a little easier to run by narrowing down our range of time period instead of using all of the data.

Udacity doesn't have a license to redistribute the data to us. They are working on alternatives to this problem.

For all the examples, we used Apple's stock (AAPL). If we tried to graph all the stocks, it would have been too much information.

<a id='3'></a>
### Trading Strategy

<a id='4'></a>
### Performance of Portfolio

<a id='5'></a>
### Statistical Tests

<a id='5_1'></a>
#### Annualized Rate of Return

<a id='5_2'></a>
#### T-test

<a id='6'></a>
### Conclusion

<a id='7'></a>
### Files

- `helper` and `project_helper` module contain utility functions and graph functions.

- `project_tests` contains unit tests for all the problems

- `tests` is used to construct test cases for unit tests.

<a id='8'></a>
### Libraries

Necessary libraries are mentioned in `requirements.txt`:

- colour==0.1.5

- cvxpy==1.0.3

- cycler==0.10.0

- numpy==1.13.3

- pandas==0.21.1

- plotly==2.2.3

- pyparsing==2.2.0

- python-dateutil==2.6.1

- pytz==2017.3

- requests==2.18.4

- scipy==1.0.0

- scikit-learn==0.19.1

- six==1.11.0

- tqdm==4.19.5