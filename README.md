# gekko-buyatsellat
Simple strategy to buy and sell assets at pre-defined thresholds with Gekko

This is a simple strategy which I have created in order to work with [Gekko Trading bot](https://github.com/askmike/gekko)

**If you like the strategy, please feel free to donate some BTC to 1M7QRQ79h4ujQMMfbqk72QnXmRdwpyLVXn**

This strategy can be configured to do below things -

1. It should sell when the price surges to x% of the bought price, i.e. profit limit.
2. It should sell when the price drops below y% of the bought price, i.e. stop loss.
3. It should buy again if the price surges to z% of the sold price.
4. It should buy again if the price goes down to u% of the sold price.

**If you want to run Gekko via command line**

You will need to change below 4 variables in `buyatsellat.js` as per your need -
```
const buyat = 1.05; // profit limit percentage (e.g. 1.15 for 15%)
const sellat = 0.97; // amount of percentage from last buy if market goes down (e.g. 0.97 for 3%)
const stop_loss_pct = 0.95; // stop loss percentage (e.g. 0.95 for 5%)
const sellat_up = 1.01; // amount of percentage from last buy if market goes up (e.g. 1.01 for 1%)
```

Copy the strategy file to /gekko/strategies folder.

Also, you will need to make below changes in `config.js` -
In `config.tradingAdvisor` module, put `buyatsellat` as method, just like -
```
config.tradingAdvisor = {
enabled: true, 
method: 'buyatsellat', 
candleSize: 60, 
historySize: 2,
```
You can use any candle size you want. They are in Minutes.

After these changes, you can run Gekko by executing -
`node gekko --config config.js`

**If you want to run Gekko in UI mode**

Copy `buyatsellat_ui.js` file to /gekko/strategies folder.
Copy `buyatsellat_ui.toml` file to /gekko/config/strategies folder. (This file is used to change parameters in UI mode)

Run Gekko in UI mode by executing -
`node gekko --ui`

Do let me know of any issues.
