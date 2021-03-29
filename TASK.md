# Snowflake Data Engineer Tech Test

## Introduction

This assessment is designed for candidates to demonstrate their knowledge of good software and data engineering practices. The task should take 30-40 minutes to complete, we are interested in how you approach a problem, go about solving it and communicating your solution; it is not designed to catch you out.

You can use Python to generate the required sample data (instructions for installing python on your machine, are in the links below). Please refer to the [README.md](./README.md) for instructions.

### Test Instructions
The purpose of this exercise is to complete a simple data warehouse in Snowflake, load data and produce a view of an aggregate query to find useful insights.

You will require a [Snowflake account](https://www.snowflake.com/); creating a trial account is free and simple to set up. Feel free to take the account creation off screen when entering any sensitive information like your email address.

## Tech Test
User Story

> The supermarket, BigSupe, has a new data source detailing which products each customer has bought in a given visit. The BI team require the data to be ingested and access set up through Snowflake; after ingestion the BI team need assistance in building a view which returns the most popular products by purchase count. Once this report has been created, the supermarket manager, Simon Skinner, will require access to the view.

The input data sources are comprised of customers (in CSV format), transactions in the form of products bought in a session (in JSON Lines format) and products (in CSV format). Their details are presented below:

**Customers**  
Contains information about customers such as the customer id and the date when they joined:

| customer_id | customer_name | loyalty_score |
| ----------- | ------------- | ------------- |
| C1          | Martha Stubbs | 7             |


**Transactions**  
Is an ever-increasing data source that currently contains a number of months of transactions.

Each transaction contains the customer id, details of what products they viewed and the date of the session:

```json
{
    "customer_id": "C1",
    "basket": [
        {
            "product_id": "P3",
            "price": 506
        },
        {
            "product_id": "P4",
            "price": 121
        }
    ],
    "date_of_purchase": "2018-09-01 11:09:00"
}

```

**Note**: when uploading the files, you may wish to combine them first. Do this with a language of your choice or with Bash, use the following:

    cat **/*.json > files.json


**Products**  
Contains information about products such as the product id, model and make of a vehicle:

| product_id | product_description | product_category |
| ---------- | ------------------- | ---------------- |
| P100       | red trousers        | clothes          |

### Acceptance Criteria

Create a simple data warehouse to ingest this data, create an RBAC model such that the BI team member Rylan can access the data.

Create a VIEW in Snowflake showing the Top 10 products viewed and give access to Rylan.

To arrive at this the following steps will need to be completed:

* Create a database to house the data
* Create schemas for the data upload, separating any sensitive data
* Create tables for the data concerned
* Upload the data
* Create a view for the top 10 products sold.

For example:

| product_id | product_category | product_description | purchase_count |
| ---------- | ---------------- | ------------------- | -------------- |
| P17        | clothes          | women's black socks | 11             |
| P04        | house            | shower gel          | 5              |
| P22        | fruit_veg        | avocado             | 7              |


* Create a view containing the count of each product sold for each user.

For example:

| customer    | customer_name | loyalty_score | product_id | product_category | purchase_count |
| ----------- | ------------- |-------------- | ---------- | ---------------- | -------------- |
| C1          | Agnes Sather  | 7             | P2         | F                | 11             |
| C1          | Agnes Sather  | 7             | P3         | H                | 5              |
| C2          | Amber Dryden  | 4             | P9         | H                | 7              |

* Create a user and role for Simon, assign grants to the raw data uploaded and to the new view
