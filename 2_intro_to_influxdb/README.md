# 2. Introduction to InfluxDB (45-60 min) 9:30-10:30

* Getting Started with Time-Series Data
* Marketing about other products
* The InfluxDB Data Model

## By the end of this section students will be able to...

* Describe what timeseries data is and recognize its use cases.
* Explain the differences between InfluxDB and other timeseries databases.
* Describe the InfluxDB data model (series vs measurement vs tags vs fields).
* Write data into InfluxDB using the InfluxDB CLI.

## Quiz (20 min) 10:30-10:50
* Questions about the InfluxDB data model

## Question 1: 
What is the difference between regular and irregular time series?

* Regular: has a fixed interval that points come in
* Irregular: can come in when they want

## Question 2: 
What are the names of the InfluxDB components on the graph on the screen? Additionally, please describe the roles of each of the components.

* measurement - what is being recorded
* tagset - tags that are acommpanying the measurement
* fieldset - what this measurement relates 
* timestamp - a time stamp

## Question 3: 
What types of values can be stored as tag values?

* Strings

## Question 4: 
What types of values can be stored as field values?

* bool
* string
* int
* floats

## Question 5: 
What is the collection of all of the tags called?

* tagset

## Question 6: 
What is the collection of all of the fields called?

* fieldset

## Question 7: 
What is the maximum number of tags that InfluxDB allows?

* 2^63


## Question 8: 
What is the maximum number of fields that InfluxDB allows?

* 2^63

## Question 9: 
What is a series?

* measurement + tagset

## Question 10:
Express a point in line protocol that has *measurement* `rainfall`, 3 *tags* `location=sf`, `meter_id=5a`, and `weather=sunny`, and 2 *fields* with keys `total` (float64), `is_raining` (bool).

* `rainfal, location=sf meter_id=5a weather=sunny total=64.3213f is_raining=true`
