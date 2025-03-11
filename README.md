# somya_202401100300250
Stock Price Movement Analysis
Overview
This project involves analyzing stock price movements using historical data. The code calculates and visualizes various stock metrics such as Moving Averages, Daily Returns, and Cumulative Returns. The analysis helps in understanding how the stock price changes over time and provides insights into market trends.

Requirements
Python: Make sure you have Python installed on your machine.
Libraries:
pandas: For data manipulation and analysis.
matplotlib: For plotting and visualizing the data.
You can install the required libraries using the following command:

bash
Copy
pip install pandas matplotlib
Files
stock_data.csv: A CSV file containing historical stock data. The CSV should have at least the following columns:
Date: The date of the stock data.
Close: The closing price of the stock for that date.
Steps to Run the Code
Load the stock data: The script loads historical stock data from a CSV file. Make sure to replace the file_path variable with the actual path to your CSV file.

Data Preparation:

Converts the Date column to a datetime format for easier analysis.
Sorts the data by Date so that the analysis follows chronological order.
Sets the Date column as the index for the dataframe.
Moving Averages:

The code calculates the 20-day and 50-day moving averages of the stock's closing price. Moving averages help smooth out short-term fluctuations and identify trends.
Daily and Cumulative Returns:

Daily Returns: The percentage change in the stock price from one day to the next.
Cumulative Returns: The overall return, assuming all daily returns are reinvested over time.
Visualizing the Results: The code generates three different plots:

Stock Price with Moving Averages: This graph shows the actual stock closing price along with the 20-day and 50-day moving averages.
Daily Returns: This plot displays daily returns, showing how much the stock price has increased or decreased each day.
Cumulative Returns: This graph shows how the stock's cumulative return changes over time, assuming all daily returns are reinvested.
Code Breakdown
python
Copy
import pandas as pd
import matplotlib.pyplot as plt
pandas is used for handling and processing data.
matplotlib is used for plotting the graphs.
python
Copy
# Load stock data from CSV
file_path = "/content/stock_data.csv"  # Replace with your actual CSV file path
df = pd.read_csv(file_path)
The script loads the stock data from a CSV file using pandas.read_csv().
python
Copy
# Convert Date column to datetime format
df['Date'] = pd.to_datetime(df['Date'])
Converts the Date column to datetime format for better date-based analysis.
python
Copy
# Sort the data by Date
df = df.sort_values('Date')
Sorts the data by the Date column to ensure chronological order.
python
Copy
# Set Date as index
df.set_index('Date', inplace=True)
Sets the Date column as the index of the dataframe for easier time-series analysis.
python
Copy
# Calculate Moving Averages
df['20-day MA'] = df['Close'].rolling(window=20).mean()
df['50-day MA'] = df['Close'].rolling(window=50).mean()
Calculates the 20-day and 50-day moving averages of the stock's closing prices.
python
Copy
# Calculate Daily Returns
df['Daily Return'] = df['Close'].pct_change()
Calculates the daily percentage change in the stock's closing price.
python
Copy
# Calculate Cumulative Returns
df['Cumulative Return'] = (1 + df['Daily Return']).cumprod()
Calculates the cumulative return, which assumes reinvestment of daily returns.
Plots
Stock Price with Moving Averages: This plot displays the stock's closing price and its 20-day and 50-day moving averages.

Daily Returns: This plot shows the daily percentage change in stock prices.

Cumulative Returns: This plot shows the total return, assuming daily returns are reinvested over time.

Example Output
The code will display three graphs:

Stock Price Movement with Moving Averages.
Daily Returns.
Cumulative Returns Over Time.
Example Plot 1: Stock Price with Moving Averages
This graph shows the stock price alongside its 20-day and 50-day moving averages.

Example Plot 2: Daily Returns
This graph shows how the stock price fluctuates on a daily basis (positive or negative return).

Example Plot 3: Cumulative Returns
This graph shows how the stock's value grows over time if daily returns were reinvested.

Conclusion
This analysis is useful for understanding the historical performance of a stock and identifying trends through moving averages and returns analysis. It can be used for making informed decisions in trading or investing. The daily and cumulative return plots are especially helpful in evaluating the overall profitability of an investment over time.

Feel free to modify the code to analyze other stock data or adjust the window size for moving averages.
