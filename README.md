
# Project Title

powerbi HOUSING DATA(DATA SOURCE ,GOOGLE BIGQUERY) PROJECT

# powerbi-Dashboard

### Dashboard Link : https://app.powerbi.com/groups/baaf03d9-5d55-48e5-b5d3-adae3eafd7da/reports/f1a1ebac-26a3-4ec4-927f-1ab6389fce66/c654eebad28ee0055774?experience=power-bi

## Problem Statement

this is a 3 page housing data dashboard visual project using powerbi to analize and creat useful dashboard to  get valuable insight into the housing and real estate market,for this powerbi prject we will be using dax measures to perform calculations and creating additional columns to help us achieve our goal which is ti help the company get valuable of all possible data driven possibility so they can make the best financial decision at the least posible time.


### Steps followed 
page 1 title housing market overview

- Step 1 : Load data into Power BI Desktop, dataset is a csv file(datasource google BIGQUERY).

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

- Step 4 : It was observed that in none of the columns errors & empty values were present except column names "annual inflation rate" and interest rate.

- Step 5 : For calculating average , null values were taken into account and replace by the median value 1.47 and 1.84 for both columns respectively. 

- Step 6 : on page 1 named housing market overview year on year (yoy) growth was calculated using das fucntion to help represent year on year growth by the sale type as follow using DAX fucntions <img width="1795" height="621" alt="Image" src="https://github.com/user-attachments/assets/40b45e66-1d64-4fcb-94a7-c7de85fa3833" />" 
and a line chart was use as visualisation to explaing this insight.(find image below)
<img width="1330" height="446" alt="Image" src="https://github.com/user-attachments/assets/c8ec2511-54c5-4ce6-9dc7-1617ab800b95" />

- step 7 : an offer column was added to help understand the fluctuation between offers nd purchase price using DAX expression (offer price = (100 * housing[purchase_price])/(100 - housing[%_change_between_offer_and_purchase])) and a scatered plot visual was use to explain the relation between offer and purchase price ith a few outlairs observe(find image below)
<img width="1602" height="825" alt="Image" src="https://github.com/user-attachments/assets/a2607fea-8bce-46fb-8808-52d7ddf176b0" />

- step 8: the median price change was calculated using the following DAX expression(medianxprice = var currmedianprice = MEDIANX(FILTER(housing,YEAR(housing[date].[Date]) = YEAR(MAX(housing[date].[Date]))),housing[purchase_price])
VAR premedianprice =  MEDIANX(FILTER(housing,YEAR(housing[date].[Date]) = YEAR(MAX(housing[date].[Date])) - 1),housing[purchase_price])
RETURN
IF(premedianprice<> 0 ,currmedianprice - premedianprice / premedianprice, BLANK()))
and a stacked bar chart was use to expain the median price change by various regions(image below)<img width="1652" height="787" alt="Image" src="https://github.com/user-attachments/assets/d5de737b-31c9-428b-b299-bddaceb0ed96" />

- step 9 :total unit sold quaterly was calculated using dax expression unite sold = CALCULATE(DISTINCTCOUNT(housing[house_id]),YEAR(housing[date]) = YEAR(MAX(housing[date])) && QUARTER(housing[date]) = QUARTER(MAX(housing[date])))
and a card visual was use to represent that inside
(image below)<img width="177" height="161" alt="Image" src="https://github.com/user-attachments/assets/c6b3565f-5e29-40b1-beed-6b21b418f5f3" />

-step 10 : last 12 months sale was calculated using dax expression (last12monthssale = CALCULATE(SUM(housing[purchase_price]),DATESINPERIOD(housing[date].[Date],MAX(housing[date]),-12,MONTH))) and another card visual was use to represent this insight (image below)
<img width="400" height="213" alt="Image" src="https://github.com/user-attachments/assets/a0249fcb-4c7a-4265-95d1-ee42166ec9b8" />

page 2 titile sale performance

-step 1 : total sale by different region was calculated using DAX expression (sale by region = CALCULATE(SUM(housing[purchase_price]),ALLEXCEPT(housing,housing[region]))) to explain how sale changes for different region and a stacked bar chart was as visual to explain this insight (image below)
<img width="1757" height="791" alt="Image" src="https://github.com/user-attachments/assets/3b61d31c-4549-465c-84c2-081cc0ed97d1" />

step 2 : total year sales to date(totalytd) was calcu;ated to explain to the fluctuation of sales for an entire year using Dax measure (totalytd sale = TOTALYTD(SUM(housing[purchase_price]),housing[date].[Date])) and a table card vissuals was use to represent this insight (image below)
<img width="387" height="675" alt="Image" src="https://github.com/user-attachments/assets/55ceb57c-2c46-4f31-9dc1-cea94d6d9f5a" />

- step 3 : average price per square meter (sqmprice) was calculated using dax expression to give and insight in average cost per sqmprice for different region (average price per sqm = AVERAGE(housing[sqm_price])) and  a donut chart was chosen as visuals to explain this insight (image below)
<img width="858" height="934" alt="Image" src="https://github.com/user-attachments/assets/73a37b3d-2d78-4724-9a96-1b0e194174e3" />

- step 4 : added house age column  to give insight on key influencers using Dax expression(house_age = ABS(YEAR(housing[date].[Date] - housing[year_build]))) and a key influencer slide visual was use to represent how house age influences the offer price and price per sqm (image below)
<img width="1271" height="792" alt="Image" src="https://github.com/user-attachments/assets/dd8f3b59-bd4d-4fa8-8245-f53e9f901d0e" />

- page 3 title sale and comparison vissuals

- step 1 adding a clustered bar chart to show average offer as it relates to purchase price (image below)
<img width="673" height="894" alt="Image" src="https://github.com/user-attachments/assets/0915c4e3-a42a-4798-aec6-97c7afccda01" />

- step 2 :adding a stacked bar chart to represent offer to sqm price relationship using Dax(offerprice to sqmprice = DIVIDE(SUM(housing[offer price]),SUM(housing[sqm]))) and visual representation can be found below
<img width="306" height="569" alt="Image" src="https://github.com/user-attachments/assets/7da20c23-d1be-4986-8203-b8b4be6e1937" />

-step 3 :adding a combo chart (line and stacked bar chart) to explain sqm per region to sqm price d1beimage can be found below
<img width="328" height="589" alt="Image" src="https://github.com/user-attachments/assets/a32d42d0-3679-4da7-a0e1-7a0a522fe5f2" />

       conclusion 

when you go through al the stage and steps taking to complete this project one will see how powerbi query editor and  powerbi dashboard can be use to clean and structure data such thst it can be use to give valuable insight to an organisation for the best possible decision making process.
