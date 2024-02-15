# EA Pivot SR MT5

This code is an Expert Advisor (EA) for MetaTrader 5 (MT5) that uses the Pivot Point system to place intraday pending orders based on support and resistance levels. The EA is designed to run on the daily chart and will delete any pending orders from the previous day before placing new ones.

## Features

- Plots support and resistance levels using Pivot Point calculations.
- Places intraday pending orders with customizable lot size, stop loss, and take profit levels.
- Implements a risk management strategy based on a percentage of the account balance.
- Limits the maximum number of pending orders that can be placed.

## Requirements

- MetaTrader 5 platform

## Inputs

- **IntradayOrdersDelay**: Delay in hours before placing intraday pending orders.
- **LotSize**: Lot size for pending orders.
- **SL**: Stop loss in pips.
- **TP**: Take profit in pips.
- **RiskPercentage**: Risk percentage per trade.
- **MaxOrders**: Maximum number of pending orders.

## How it Works

The EA runs the `OnTick()` function, which is called on every tick of the chart. It first checks if it's a new trading day by comparing the current time with the last trade execution time. If it's a new day, the EA deletes all pending orders from the previous day.

Next, the EA calculates the pivot, resistance1, and support1 levels using the previous day's high, low, and close prices. It then loops through the `MaxOrders` variable and places intraday pending orders alternately between the resistance1 and support1 levels.

For each pending order, the EA calculates the stop loss and take profit levels based on the price, SL, and TP inputs. It also calculates the maximum lot size based on the risk percentage and account balance. The lot size is then set to the minimum value between the LotSize input and the maximum lot size.

Finally, the EA calls the `SendPendingOrder()` function from the Trade library to place the pending order with the calculated parameters.

On deinitialization, the EA runs the `OnDeinit()` function, which deletes all pending orders to clean up any remaining orders.

Please note that ForexRobotEasy is not the official developer of this product. We only provide sample code that is similar to the product's functionality. To find the official developer of this product, please refer to the MQL5 website.

For detailed reviews and trading results of this product, visit [EA Pivot SR MT5 Review](https://forexroboteasy.com/forex-robot-review/ea-pivot-sr-mt5-review-reliable-forex-software-with-precise-trading-results/).

For more information, please visit [Forex Robot Easy](https://www.forexroboteasy.com).
