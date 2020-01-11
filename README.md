# TimeTravel-Engineering
Original.csv is the raw data and transformed.csv is the engineered data.
The purpose of this project was to solve the issue of time snapshot/ time travel/ versioning of data .
Six new columns were added to provide HISTORY and GRANULARITY to subscription sales for each and every row(sum over last4weeks, last13weeks, last52weeks by total(3 columns) and by type & coupon (3 columns). 
Now by just querying by some dates, you can get the historical context of each and every date(upto as many weeks as you want)
 The columns can be built to aggregate by particular time intervals and/or by categorical columns. There are several other use cases such as sliding windows for intervals that change with every iteration, rank and rownumber(), 
# JUSTIFICATION:
 In terms of Big Data Architecture(particularly Redshift) it is a best practice to maintain Big Fact tables as the real power of Redshift is harnessed by having big tables. Therefore, there will be a table which will have the original raw data. This original table will be updated whenever there is an update available. This Pyspark/Python script will be applied to this updated data, and the new transformed data will be overwritten to a table in S3(storage is cheap) and then eventually Redshift Spectrum can be used to query the data by date(optimized as table is partioned by date) and automaically be provided time travel columns. 
 The script written in pyspark/python will be implimented using AWS Glue. 
 BI Analyst can use this transformed and enriched data to get a complete picture of the company's performance.
 Data Scientists can use this transformed and enriched data to train robust forecasting algorithims. 
PS. If for some reason engineers do not want to keep all the data going back to 2/3 years ago, they can retain the information using the method(time windows) above without having to save all of it. 
