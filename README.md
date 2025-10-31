# Wall-Street-Bet-Trading-Bot
<p align="center">
  <img width="300" height="300" alt="Trading_Bot_Logo" 
       src="https://github.com/user-attachments/assets/faf88873-e8c2-4160-aa38-b93a45541e09" />

</p>

# WSB Sentiment Trading Bot
#### Just a fun project I made in my free time after seeing someone try to trade based on advices from r/WallStreetBets — and lose all their money. So I decided to build a bot that does the opposite of what r/WallStreetBets says. What is the worst things that could happen?

---

## Table of Contents
- [Description](#description)
- [Demo](#demo)
- [Key Features](#key-features)
- [Built With](#built-with)

---

## Description
This bot uses the **Reddit API** (`praw`) and the **Alpaca API** to simulate trading based on posts from the Reddit user `wsbapp` in their daily “What Are Your Moves Tomorrow” threads.  

The bot works as follows:  
1. It pulls all comments from the latest thread.  
2. Each comment is scanned for stock tickers from a predefined list.  
3. Sentiment analysis is applied using **VADER** (`sia.polarity_scores`) to score the comment as positive (`1`) or negative (`-1`) for the stock.  
4. The bot then executes trades based on **contrarian sentiment**:
   - If the comment predicts the stock will go up → the bot shorts the stock.  
   - If the comment predicts the stock will go down → the bot buys the stock.  
5. For shorted stocks, the bot keeps track of the **stock’s current price** and the **number of shares shorted**.  
6. Every 60 seconds, `check_signals_and_trade()` runs to check whether any shorted stock has dropped in price so it can be bought back, ensuring the bot can close all positions profitably.  

This approach combines sentiment analysis and automated trading to simulate a basic contrarian trading strategy based on community sentiment from Reddit.

---

## Demo
### 1. Trades being executed
<img width="1476" height="957" alt="image" src="https://github.com/user-attachments/assets/c8b675a8-6ce2-49d9-8406-2a2c050f43b6" />

### 2. Sentiment Sorted with Matplotlib 
<img width="951" height="863" alt="image" src="https://github.com/user-attachments/assets/a431e46e-cd0d-4c2d-95c1-d99ad2cc1ae8" />


![Trading Bot Demo](https://github.com/your-username/your-repo/raw/main/assets/trading_demo.gif)

---

## Key Features
* **Reddit Integration:** Pulls weekly posts and comments from `wsbapp`.
* **Sentiment Analysis:** Uses VADER to label comments as positive, neutral, or negative.
* **Stock Extraction:** Matches words in comments to a predefined list of stock tickers.
* **Automated Paper Trading:** Submits buy or sell orders using Alpaca’s API.
* **Short Position Tracking:** Tracks short positions and prices to execute buybacks if profitable.
* **Data Visualization:** Generates bar plots showing sentiment distribution.

---

## Built With
* **Core Language:** Python 3
* **Reddit API:** `praw`
* **Alpaca API:** `alpaca-trade-api`
* **Sentiment Analysis:** `nltk` (VADER), `TextBlob`
* **Data Handling:** `pandas`
* **Visualization:** `matplotlib`, `seaborn`
* **Other Libraries:** `re`, `csv`, `time`, `collections.defaultdict`

---
