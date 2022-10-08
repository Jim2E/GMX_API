# GMX_API

Is there a free way to get less than 1m data for [eth,btc,uni,link,usdc,frax]? If so, how much can we reduce latency in price updates? I use the GMX API to fetch prices. According to their site: https://gmx-io.notion.site/gmx-io/GMX-Technical-Overview-47fc5ed832e243afb9e97e8a4a036353:
"The [PriceFeed](https://github.com/gmx-io/gmx-contracts/blob/master/contracts/oracle/FastPriceFeed.sol) contract accepts submissions from the price feed keeper. This keeper calculates prices using the median price of Binance, FTX and Bitfinex. There are two types of keepers:

- Price feed keeper: submits prices routinely for swaps
- Position keeper: submits prices when executing a position

The vault uses the price from the keeper if it is within a configured percentage of the corresponding Chainlink price. If the price exceeds this threshold then a spread would be created between the bounded price and the Chainlink price, this threshold is based on the historical max deviation of the Chainlink price from the median price of reference exchanges. For example, if the max deviation is 2.5% and the price of the token on Chainlink is $100, if the keeper price is $103, then the pricing on the vault would be $100 to $103. When opening a long position, the higher price is used and when closing the lower price is used, for short positions, the lower price is used when opening and the higher price is used for closing."

It's still not exactly clear what consensus is on the latency of the updates but eyeball comparing to the freely-available 1m data on TradingView, the candles are not 100% off. There is definetly inaccuracies, obvious from the plateaus on the 1s plot. The error is due to the pricing update latency on GMX's API. It is also due to the way I defined Open and closes for each candle. I am not sure what is the rule behind open/close price times on TradingView because it seems arbitrary IMO, but this is an important question I need to resolve because during times of volatility, this can make or break a strategy. I will improve this to improve my understanding of price oracles but someone can definetly use this as a starting point to work with some of the data GMX has to offer.

