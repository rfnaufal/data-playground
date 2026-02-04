### Loading Data to BigQuery

Preparation:

Download [`NYC taxi 2018 trips data`](https://storage.googleapis.com/cloud-training/OCBL013/nyc_tlc_yellow_trips_2018_subset_1.csv)

#### Task 1. Create a new dataset to store tables

Create dataset and name nyctaxi other setting leave as default.

#### Task 2. Ingest a new dataset from a CSV

Create Table

```
Specify the below table options:

Source:

Create table from: Upload
Choose File: select the file you downloaded locally earlier
File format: CSV
Destination:

Table name: 2018trips Leave all other settings at default.
Schema:

Check Auto Detect (tip: Not seeing the checkbox? Ensure the file format is CSV and not Avro)
```

**Running SQL Queries**

list the top 5 most expensive trips of the year:

```sql
#standardSQL
SELECT
  *
FROM
  nyctaxi.2018trips
ORDER BY
  fare_amount DESC
LIMIT  5
```

#### Task 3. Ingest a new dataset from Google Cloud Storage

In your Cloud Shell: 

```
bq load \
--source_format=CSV \
--autodetect \
--noreplace  \
nyctaxi.2018trips \
gs://cloud-training/OCBL013/nyc_tlc_yellow_trips_2018_subset_2.csv
```

#### Task 4. Create tables from other tables with DDL

Create Table:

```sql
#standardSQL
CREATE TABLE
  nyctaxi.january_trips AS
SELECT
  *
FROM
  nyctaxi.2018trips
WHERE
  EXTRACT(Month
  FROM
    pickup_datetime)=1;
```

find the longest distance traveled in the month of January:

```sql
#standardSQL
SELECT
  *
FROM
  nyctaxi.january_trips
ORDER BY
  trip_distance DESC
LIMIT
  1
```
