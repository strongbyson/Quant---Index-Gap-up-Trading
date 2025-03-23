# Gap-Up Trading Strategy for NIFTYBEES Using Bollinger Bands %B

## Overview
This project implements a **Gap-Up Trading Strategy** for the NIFTY Index ETF (NIFTYBEES) using the Bollinger Bands %B technical indicator. The strategy aims to capitalize on short-term price movements by buying and selling NIFTYBEES based on specific %B conditions over a 6-year historical dataset.

---

## Data
- **Dataset**: 6 years of OHLC (Open, High, Low, Close) data for NIFTYBEES (NIFTY ETF).
- **Source**: GOOGLE FINANCE
- **Time Period**: March 2019 to March 2025].
- **Indicator**: Bollinger Bands %B, calculated using the daily closing prices with a 20-day period and a standard deviation multiplier of 2.

## Trading Strategy

### Buying Condition
- **Trigger**: Buy NIFTYBEES at the **close price** of the current day if:
  1. The current day’s %B is **greater than 0.40**.
  2. The current day’s %B is **greater than the previous day’s %B**.
- **Units to Buy**:
  \[
  \text{Units Bought} = \text{floor}\left(\frac{\text{Total Capital}}{\text{Close Price}}\right)
  \]
  - `Total Capital`: Available capital for trading (user-defined).
  - `Close Price`: Closing price of NIFTYBEES on the buy day.
  - `floor`: Rounds down to the nearest whole number (0 decimal places).

### Selling Condition
- **Trigger**: Sell **all units bought** at the **open price** of the next trading day.
- **Profit Calculation**:
  \[
  \text{Profit} = \text{Units Bought} \times (\text{Sell Price} - \text{Buy Price})
  \]
  Where:
  - `Sell Price`: Open price of the next day.
  - `Buy Price`: Close price of the buy day.

---

## Implementation
- **Language**: Python (or specify another language if used).
- **Libraries**:
  - `pandas`: For data manipulation and calculations.
  - `numpy`: For numerical operations (e.g., rounding units).
  - `ta-lib` or `pandas-ta`: For calculating Bollinger Bands and %B (specify which library you used).
- **File Structure**:
  - `niftybees_data.csv`: Historical OHLC data for NIFTYBEES.
  - `strategy.py`: Main script implementing the trading strategy.
  - `niftybees_export.csv`: Output file with trading results (includes columns like Open, High, Low, Close, %B, Units Bought, Buying Price, Selling Price, Profit, etc.).

---

## Results
- **Output**: The strategy generates a CSV file (`niftybees_export.csv`) with the following columns:
  - `Open`, `High`, `Low`, `Close`: OHLC prices.
  - `bband_lower`, `bband_upper`, `%b`: Bollinger Bands and %B values.
  - `Trade Counter`, `Units Bought`, `Buying Price`, `Selling Price`, `Profit`: Trading metrics.
  - `Total Units`, `Units Sold`, `Available Capital`, `Buying Amount`: Additional tracking metrics.
- **Performance**: We started with initial capital of INR 1 million, over 6 years, the strategy executed 349 trades, out of wich 289 were profit trades with average profit of INR 415,454 per trade, 48 loss trades with average loss of 185,988 per trade, and 12 trades were with nil profits.

---

## Notes
- **Risk Warning**: This strategy is for educational purposes only. Trading involves significant financial risk, and past performance is not indicative of future results.
- **Improvements**:
  - Add stop-loss or take-profit conditions to manage risk.
  - Backtest with different %B thresholds or Bollinger Band parameters.
  - Incorporate transaction costs (e.g., brokerage fees) for more realistic results.
- **Data Cleaning**: Ensure the OHLC data is clean (e.g., no missing values) before running the strategy.

---

## Contributing
Contributions are welcome! Please fork the repository, make your changes, and submit a pull request. For major changes, open an issue first to discuss your ideas.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Let me know if you’d like to add more details or sections to the README!
