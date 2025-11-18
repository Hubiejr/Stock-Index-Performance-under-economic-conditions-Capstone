# Stock Index Performance under economic conditions (Capstone)

## Table of Contents
* [Motivation](#motivation)
* [Technologies Used](#technologies-used)
* [Main Question](#MAIN-QUESTION)
* [Questions](#questions)
* [Python Code](#MAIN-Jupyter-Notebook-file)
* [Functions](#ALL-FUNCTIONS-AND-ALL-USEAGES)
* [Data Sources](#Data-Sources)


## Overview 
This project touches on the stock market sectors, **tech**, **healthcare**, and **energy**, etc.. and show which one performs best under certain economic conditions.

## Motivation
For motivation, I love looking into the stock market and looking at and potentially predicting what may happen next. I haven't touched it in a while. I recently got back into it. I used to do a lot of option trades, but they got too risky, and you usually make some good money, but the problem is you might lose your stock. Now I'm into ETFs and Mutual funds; they are much safer. So with this project, I was thinking about doing the tech sector in the stock market and showing how interest rates affect stock movements 

### Technologies used
- **Python** (data analysis and visualization)
- **Pandas / NumPy** (data manipulation)
- **Matplotlib / Seaborn** (visualization)
- **Jupyter Notebook** (IDE)
- **POWERPOINT** (PRESENTATION)
- **Git** (version control)

# MAIN Jupyter Notebook file
``CleanVisualization.ipynb``

## MAIN QUESTION:
## Which stock indexes (tech, healthcare, energy, etc.) perform best under certain economic conditions (inflation, recession, recovery, etc.) 

## Questions
1) How did COVID affect inflation, and where it recovered?
2) What stocks are considered tech, healthcare, and energy?
3) What is the difference between Indexes and Sectors?
4) What is the October Effect?






# ALL FUNCTIONS AND ALL USEAGES

## CLEANUP FUNCTIONS

###  ``` clean_data(df, index_name = NONE)```
       gets rid of commas, and percentages, converts numeric to floats
       
       (USEAGE) 
              tech = clean_data(tech, "NAME")

              LOOPING (IF YOU HAVE MULTIPLE)
              csvlist = [tech,health]
              namelist = ['Technology','Healthcare']
              for i in range(len(csvlist)):
                csvlist[i] = clean_data(csvlist[i],namelist[i])
              tech, health = csvlist

###  ```clean_inflate(df)```
       specifically for inflation 
       changes string to date_time
       
       (USEAGE) 
              clean_inflate(inflation)

###  ```change_year(df,year)```
       For changing the year of an index
       mainly paired with a graphing function

       (USEAGE)  
              tech2020 = change_year(tech,2020)

###  ```change_month_year(df,month,year)```
       Changes the month and the year
       (Didnt really use in this project could be usefull though)
       
       (USEAGE) 
              techmarch2020 = change_month_year(tech,3,2020)


## LOGICAL FUNCTIONS

###  ```index_avg(df)```
         Made to compare inflation averages for each month
         It will average a price for that month
         Example
             2025-01-01	686.837000
             2025-02-01	684.565789
             2025-03-01	686.234286
             
       (USEAGE)
              techavg = index_avg(tech)


## PRETTY GRAPH FUNCTIONS (BEST GRAPHS TO USE)

###  ```pretty_multi_graph(dfs, labels, title)```
        Mainly used for comparisions with a whole bunch of indexes
        USED yearly index functions to make an easy comparison
        
       (USEAGE)
            # make sure you have 2 lists for this to work
             dfs2020 = [tech2020,health2020,house2020,energy2020,indust2020]
             labels2020 = ['Technology', 'Health', 'Real Estate', 'Energy', 'Industrials'
             multi_graph(dfs2020, labels2020, "Price Comparision 2020")
      
###  ```mcomp_graph_stacked(df1, lab1, df2, lab2)```
        Month Comparision of 2 dataframes PRETTY VERSION
        inside the graph on the bottom it will show the months of the year
        
       (USEAGE)
               mcomp_graph_stacked(tech2020, "Tech 2020", tech2025, "Tech 2025")

###  ```comp_graph_stacked(df1, lab1, df2, lab2)```
        Year Comparision of 2 dataframes PRETTY VERSION
        Shows the years instead of months
        
       (USEAGE)
               comp_graph_stacked(tech2020, "Tech 2020", tech2025, "Tech 2025")

###  ```comp_graph_dual(df1, lab1, df2, lab2, show_change=False)```
        Shows 2 Functions in one graph 
        show_change shows a percentage comparision if set to TRUE
        
       (USEAGE)
              #shows two graphs if show_change = true 
              #if false it will only show the first one
              comp_graph_dual(tech, "Tech Index", inflate, "Inflation", show_change=True)

###  ```mcomp_graph_dual(df1, lab1, df2, lab2, show_change=False)```  (MAINLY WHAT I USED FOR MY POWERPOINT)
        Month on the bottom of the graph instead of year
        Shows 2 Functions in one graph 
        show_change shows a percentage comparision if set to TRUE
        
       (USEAGE)
              #shows two graphs if show_change = true 
              #if false it will only show the first one
              mcomp_graph_dual(tech, "Tech Index", inflate, "Inflation", show_change=True)

 
 ###  ```save_mcomp_graph_dual(df1, lab1, df2, lab2, show_change=False)```  (FOR SAVING ONLY)
       Saves an image of mcomp graph
       didnt really use but can be handy 
       
       (USEAGE) 
              if change = false
              fig = save_mcomp_graph_dual(inflate, "Inflation avg", techavg, "Tech avg", show_change=False)
              fig.savefig('Inflation_Graphs/tech_vs_inflation.png')
              plt.show()
             
              if change = true
              fig1, fig2 = save_mcomp_graph_dual(inflate, "Inflation avg", techavg, "Tech avg", show_change=True)
              fig1.savefig('Inflation_Graphs/tech_vs_inflation_main.png')
              fig2.savefig('Inflation_Graphs/tech_vs_inflation_change.png')
              plt.show()

  

## BASIC GRAPH FUNCTIONS

###  ```graphing(df,indx_name)```
        Makes a graph of an index
        
       (USEAGE) 
              graphing(tech, "Technology")
       
###  ```year_graph(df,indx_name,year)```
        Makes a graph of an index of that specific year
        
       (USEAGE)
              year_graph(energy, "Energy", 2022)
       
###  ```comp_graph(df1, lab1, df2, lab2)```
        Comparision of two dataframes graph Function depending on Date and Price
        
       (USEAGE)
              comp_graph(tech,"Technology", health, "Healthcare")

###  ```mcomp_graph(df1, lab1, df2, lab2)```
        Month Comparision of 2 dataframes
        
       (USEAGE)
              mcomp_graph(tech,"Technology", health, "Healthcare")

###  ```multi_graph(dfs, labels)```
        Comparison of all dataframes 
        Needs some form of list
        
       (USEAGE)
             dfs = [tech,health,house,energy,indust]
             labels = ['Technology', 'Health', 'Real Estate', 'Energy', 'Industrials']
             multi_graph(dfs, labels)

  
## Data Sources


## Technology index
https://fred.stlouisfed.org/series/NASDAQNDXX
https://www.investing.com/indices/s-p-500-information-technology-historical-data




## Electric Index
https://fred.stlouisfed.org/series/PNRGINDEXM
https://www.investing.com/etfs/proshares-sp-500-ex-energy
https://www.investing.com/indices/s-p-500-energy-historical-data




## Healthcare Index
https://www.investing.com/indices/s-p-500-health-care-historical-data


## Industrials Index
https://www.investing.com/indices/s-p-500-industrials-historical-data


## Real Estate
https://www.investing.com/indices/s-p-500-real-estate-historical-data




## Explanation of what inflation is
https://www.ig.com/en/trading-strategies/how-does-inflation-affect-the-stock-market-210423


## Inflation CSV Source
https://fred.stlouisfed.org/series/CPIAUCSL


## FINDS STOCK INDEXES and makes it easy to download csv’s with account
https://www.investing.com/indices/s-p-500-health-care-historical-data





  





