# 3. Working with the CLI and Query Language (45-60 min) 11:00-12:00

* Working with the InfluxDB CLI
* The InfluxDB Query Language

## By the end of this section students will be able to...

* Query InfluxDB using the InfluxDB CLI.
* Understand the structure of the data that is returned from a query.
* Articulate what InfluxQL can do.
* Create novel queries of their own.

## Quiz (20 min) 12:00-12:20
* Querying Data (Project)


## Write the data to your instance.
```
$ curl https://s3-us-west-2.amazonaws.com/influx-sample-data/stocks.txt > stocks.txt
$ influx -import -path=stocks.txt -precision=s
```

The data that we've loaded in the data for the SP500 from 2013, but where the timestamps have been adjusted to the current time.


## Question 1:
What is the schema of the data we installed on your instance?

### Bonus: 
How many series are there?

## Question 2:
What was the highest opening stock price in the last 10 days?

## Question 3:
What company had the highest opening price in the last 10 days?

## Question 4:
What was the highest opening price for each of the last 10 days and which company had this price?

## Question 5:
How many of the last 30 days did the price of Google's stock (ticker='GOOG') go above $500?
