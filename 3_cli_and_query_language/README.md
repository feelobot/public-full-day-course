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
```
> SHOW MEASUREMENTS
name: measurements
------------------
name
stock_price

> SHOW FIELD KEYS
name: stock_price
-----------------
fieldKey
high
low
open
volume
```

### Bonus: 
How many series are there?
```
➜  ~  influx -execute "SHOW SERIES" -database "stocks" | sed '/name: .*/d' | sed '/\-\-/d' | sed '/_key/d' | sed '/^$/d' | wc -l
     524
```
## Question 2:
What was the highest opening stock price in the last 10 days?
```
> select max(open) from stock_price where time > now() - 10d
name: stock_price
-----------------
time			max
1455065191000000000	497.72
```
## Question 3:
What company had the highest opening price in the last 10 days?
```
> select max(open),ticker from stock_price where time > now() - 10d
name: stock_price
-----------------
time			max	ticker
1455065191000000000	497.72	GOOG
```

## Question 4:
What was the highest opening price for each of the last 10 days and which company had this price?
```
> select max(open), ticker from stock_price where time > now() - 10d group by time(1d)
name: stock_price
-----------------
time			max	ticker
1454976000000000000
1455062400000000000	497.72	GOOG
1455148800000000000	483.94	GOOG
1455235200000000000	488.94	GOOG
1455321600000000000
1455408000000000000
1455494400000000000	483.68	GOOG
1455580800000000000	488.37	GOOG
1455667200000000000
1455753600000000000	481.41	GOOG
1455840000000000000	467.26	GOOG
>
```
## Question 5:
How many of the last 30 days did the price of Google's stock (ticker='GOOG') go above $500?
```
> select count(high) from stock_price where ticker='GOOG' and time > now() - 30d and high > 500
name: stock_price
-----------------
time			count
1453321712652946204	5
```
