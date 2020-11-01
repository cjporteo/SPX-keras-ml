## SPX-keras-ml

LSTM recurrent neural network in Keras to classify short term SPX price action using technical dark pool indicators.

## About
This model attempts to predict one-day price action of the SPX market index (S&P 500®) using a wide range of technical indicators. By using an LSTM recurrent neural network in Keras, the model can correctly classify evenly distributed buy, sell and hold signals with **45-50% accuracy** (compared to a baseline of 33% for random guesses).

The model is *far* from deployment-ready, and, in its current state, blindly following its predicted signals is inadvisable. Next steps would be to increase the granularity of the training data (intraday instead of the current EOD) and to incorporate more qualitative financial predictors such as market sentiment.

## Features

The two most noteworthy features in this model are **DIX** and **GEX**, provided from https://squeezemetrics.com. These indicators give insight into market-makers' buying activity in dark pools, serving as an interesting proxy for investor sentiment. I'll do my best to provide a succinct (oversimplified) explanation of them both here, but for a more in-depth explanation, I suggest reading the White Paper [here](https://squeezemetrics.com/monitor/download/pdf/short_is_long.pdf?).

**DIX (Dark Index):** Dark pool short volume across all components of the S&P 500®. Higher short volume for a MM means more investors are buying. See the table below.

![enter link description](https://i.imgur.com/wrjz2DS.png)

****GEX** (Gamma Exposure):** A measure of option market-makers' hedging obligations. A high GEX means the option market is implying low volatility, while a low or negative GEX suggests potentially high volatility.

Other features used in this model include:

 - SPX
 - SPY Volume
 - VIX
 - VIX Put/Call Ratio
 - VIX Options Volume
 - SPX Put/Call Ratio
 - SPX Options Volume
 - USO (rough proxy for oil price)
 - GLD (rough proxy for gold price)
 - US Treasury Yield Rates for a variety of maturities 

I used a custom scraping script to scrape the options data from the CBOE archive and treasury data from treasury.gov.
 
 The full dataset containing EOD records for all of these predictors spans back to 2011.

# Model Architecture

![enter link description here](https://i.imgur.com/iNnafD5.png)

# Validation Accuracy by Epoch

![enter link description here](https://i.imgur.com/XWk5B19.png)
