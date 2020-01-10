# TimeTravel-Engineering
Original.csv is the raw data and transformed.csv is the engineered data.
The purpose of this project was to solve the issue of time snapshot/ time travel/ versioning of data .
Six new columns were added to provide HISTORY and GRANULARITY to subscription sales for each and every row(sum over last4weeks, last13weeks, last52weeks). 
Now by just querying by some dates, you can get the historical context of each and every date(upto as many weeks as you want)
 The columns can be engineered to perform by particular time intervals and/or categorical columns
# JUSTIFICATION:
 In terms of Big Data Architecture(particularly Redshift) it is a best practice to maintain Big Fact tables as the real power of Redshift is harnessed by having big tables. Therefore, there will be a table which will have the original raw data. This original table will be updated whenever there is an update available. This Pyspark/Python script will be applied to this updated data, and the new transformed data will be overwritten to a table in S3 and then eventually Redshift.
 The script written in pyspark/python will be implimented using AWS Glue 
 BI Analyst can use this transformed and enriched data to get a complete picture of the company's performance
 Data Scientists can use this transformed and enriched data to train robust forecasting algorithims 
PS. If for some reason engineers do not want to keep all the data going back to 2/3 years ago, they can retain the information using the method(time windows) above without having to save all of it. 
