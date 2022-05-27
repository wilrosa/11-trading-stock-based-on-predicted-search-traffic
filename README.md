# trading-stock-based-on-predicted-search-traffic-11

This repo contains the results of the module 11 challenge. To view the file, open the "forecasting_net_prophet" folder and then the "forecasting_net_prophet.ipynb" file. 

I assumed the role of a growth analyst at MercadoLibre, the most popular e-commerce site in Latin America, tasked with analyzing the company's financial and user data in clever ways to make the company grow. So, I focused on finding out if the ability to predict search traffic can translate into the ability to successfully trade the stock.

The `forecasting_net_prophet.ipynb` Jupyter Notebook file contains data preparation, analysis, and visualizations for all the time series data that the company needs to understand to drive revenue.

Specifically, I completed the following:

(1) Visual depictions of seasonality (as measured by Google Search traffic) that are of interest to the company 
(2) An evaluation of how the company’s stock price correlates to its Google Search traffic
(3) A Prophet forecast model that can predict hourly user search traffic
(4) Answers to questions in the instructions 
(5) A plot of a forecast for the company’s future revenue

## Installation Guide

First, fbprophet and its dependencies were installed into the development environment.

```python
!pip install pystan
!pip install fbprophet
!pip install hvplot
!pip install holoviews
```
---

## Technologies

This project leverages python 3.7 with the following libraries and dependencies:

* [pandas](https://github.com/pandas-dev/pandas) - For manipulating data

* [hvplot](https://github.com/holoviz/hvplot) - High-level plotting API for the PyData ecosystem built on HoloViews

* [holoviews](https://https://github.com/holoviz/holoviews) - Make data analysis and visualization seamless and simple

* [fbprophet](https://github.com/facebook/prophet) - Procedure for forecasting time series data

* [matplotlib](https://github.com/matplotlib/matplotlib) - Creating static, animated, and interactive visualizations

---

### **Step 1: Found Unusual Patterns in Hourly Google Search Traffic**

The first question is whether the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, I picked out any unusual patterns in the Google search data for the company, and connected them to corporate financial events. 

To do so, I completed the following steps:

(1) Read the search data into a DataFrame, and then sliced the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Used hvPlot to visualize the results. 

    Answered the following question: 
    
    Do any unusual patterns exist?

(2) Calculated the total search traffic for the month, and then compared the value to the monthly median across all months. 

    Answered the following question: 
    
    Did the Google search traffic increase during the month that MercadoLibre released its financial results?

### **Step 2: Mined the Search Traffic Data for Seasonality**

Here, I mined the search traffic data for predictable seasonal patterns of interest in the company. The goal was to track and predict interest in the company and its platform for any time of day, so that marketing can focus their efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget.

To do so, complete the following steps:

(1) Grouped the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).

(2) Used hvPlot, visualized this traffic as a heatmap, referencing the `index.hour` as the x-axis and the `index.dayofweek` as the y-axis. 

        Answered the following question: 
        
        Does any day-of-week effect that you observe concentrate in just a few hours of that day?

(3) Grouped the search data by the week of the year. 

        Answered the following question: 
    
        Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

### **Step 3: Related the Search Traffic to Stock Price Patterns**

Investigated if there is any relationship between the search data and the company stock price exists

To do so, I completed the following steps:

(1) Read in and plot the stock price data. Concatenated the stock price data to the search data in a single DataFrame.

(2) Sliced the data to just the first half of 2020 (`2020-01` to `2020-06` in the DataFrame), and then used hvPlot to plot the data.

        Answered the following question: 
        
        Do both time series indicate a common trend that’s consistent with this narrative?

(3) Created a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Created two additional columns:

(A) “Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility    

(B) “Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis.

(4) Reviewed the time series correlation, and then answered the following question: 

      Answered the following questions: 
      
      Does a predictable relationship exist between the lagged search traffic and the stock volatility?
      
      Or between the lagged search traffic and the stock price returns?

### **Step 4: Created a Time Series Model with Prophet**

Here, I produced a time series model that analyzes and forecasts patterns in the hourly search data. To do so, complete the following steps:

(1) Set up the Google search data for a Prophet forecasting model.

(2) After estimating the model, plotted the forecast. 

    Also answered the following questions: 
    
    How's the near-term forecast for the popularity of MercadoLibre? 
    
(3) Plotted the individual time series components of the model to answer the following questions:
    
    What time of day exhibits the greatest popularity?
    
    Which day of the week gets the most search traffic?
    
    What's the lowest point for search traffic in the calendar year?

### **Step 5: Forecasted Revenue by Using Time Series Models**

Finanlly, I forecasted the total sales for the next quarter.

To do so, complete the following steps:

(1) Read in the daily historical sales (that is, revenue) figures, and then applied a Prophet model to the data.

(2) Interpretted the model output to identify any seasonal patterns in the company's revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

(3) Produced a sales forecast for the finance group. Gave them a number for the expected total sales in the next quarter. Included the best- and worst-case scenarios for better planning.
    
---
## Contributors

Brought to you by Wilson Rosa. https://www.linkedin.com/in/wilson-rosa-angeles/.

---
## License

MIT