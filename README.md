# HVAR Data Engineer Challenge

As AI and Machine Learning take over the world, data engineering sneaks in to become one of the most important skills on the market. Absurd amounts of information became the norm for most companies, and handling all that data proved to be way more challenging than expected. This challenge is a way of testing your abilities in that field. Our objective is to give you a small taste of what a data engineer does everyday at HVAR CONSULTING.

# Scenario

To better contextualize this challenge, we will work under a fictitious, but very close to our reality, scenario. At HVAR CONSULTING, we work with a range of different companies, dealing with all kinds of data. One of our specialties is to architect, setup, implement and maintain a data driven architecture for our partners, focusing on implementing all requirements of a modern Big Data environment. What that means is allowing the creation of data driven solutions, exploring the newest technologies in the world of AI and Machine Learning, enhancing the decision making process of business intelligence, and so on. 

Let's imagine then that the company HFake is one of our newest partners. We've joined in this mission of transforming and modernizing their data platforms and solutions. HFake is a marketplace platform that allows sellers from all over the country to sell their products in one centralized, safe and easy to use platform. They're a massive company with an even bigger user base, dealing with dozens of petabytes of information. Our job is to implement all the features described above.

# The Challenge

With all that known, your challenge is to process all that data into the data architecture specifically designed by our team to our new HFake partner. Consider the requisites carefully, and implement the solutions to the best of your ability.

## Data

For this example, HFake's data will be a modified version of the [Olist Kaggle Database](https://www.kaggle.com/olistbr/brazilian-ecommerce). The data for the challenge can be found in the `data` folder, and is divided as follows:

- `olist_customers_dataset.csv`: contains customers that have bought products on the HFake marketplace.
- `olist_geolocation_dataset.csv`: contains geolocation information mapping zip codes to regions.
- `olist_products_dataset.csv`: contains products sold on the HFake marketplace.
- `olist_sellers_dataset.csv`: contains the partnered stores that sell on HFake marketplace.
- `product_category_name_translation.csv`: contains localized information of category names (Portuguese to English).
- `olist_orders.json`: contains a payload with orders made on HFake marketplace.

## Functional Requirements

The main objective of this challenge is to process and transform all that data into simple to use data marts that can be integrated to HFake's data architect. The requirements below must be followed on your implementation. Assume this is a historical load of data into the system, but periodic batches of data will also be ingested. Write your data processing pipelines taking into account that new data will come all the time, and that data must be correctly loaded, and processed. Don't forget to account for performance. The volume of data is big, so writing optimzed code is key to maintain usability.

### Data Lake

All data must be loaded into a Data Lake structure divided in four zones: 

1. the `bronze` zone should contain the raw files as received and will be used for hystorical scenarios.
1. the `silver` zone should contain deduplicated, merged, cleaned and aggregated information. It will be used by data scientists and engineers.
1. the `gold` zone should contain business ready data marts.

Files should be separated into a time partitioned folder structure.

### Data Marts

One of the key necessities for HKey when it comes to data is data science and business intelligence. This means it's very important that the data is well aggregated, easy to access and utilize. One way to do this is the creation of data marts. For this scenario, the following data marts should be created for these key users to utilize:

1. **Customer Data Mart:** must contain all the information regarding the customer, as well as the latitude and longitude of the customer's geolocated zip-code. Approximate the region's latitude and longitude for the prefix.
1. **Product Data Mart:** must contain all information regarding products. The product category in this data mart must be located to English.
1. **Order Data Mart:** must contain all information regarding an order, including all of the items acquired. Review information must not be in this data mart.
1. **Review Data Mart:** must contain all information regarding customer reviews of orders.
1. **Seller Data Mart:** must contain all information regarding sellers of the platform. This platform must also implement a calculated KPI called *Quality Score*, which must be the average of review scores of the seller.

## Non-Functional Requirements

You can use any tools at your disposal to design your solution. Document your code with both comments and guidance documents, and write easy to maintain and scalable solutions. Think of elasticity and the amount of data that will be processed. The deliverable for this challenge will be:

1. A zip file containing your solution. Structure as if pushing to a Git repository, with a `README.md` file describing your solution and design choices. Be as clear as possible!
1. Sample `csv` files of the data marts following all the requisites above.

You can send your solution directly to the email you are currently in contact with.

# Hints

+ There are many ways of writing data processing pipelines. [Google Colab](https://colab.research.google.com/github/asifahmed90/pyspark-ML-in-Colab/blob/master/PySpark_Regression_Analysis.ipynb) allows you to easily setup a PySpark environment. [Databricks Community](https://databricks.com/product/faq/community-edition) is another tool for Spark, but also other useful tools for this challenge such as Hive and a distributed file system.
+ Be clear about how and where the data should be stored and processed in an ideal scenario, make decisions and justify them accordingly.
+ [Google Cloud Patform](https://cloud.google.com/free) has a range of tools and services that can be used in its free tier, including BigQuery, which is a very usefull tool for this challenge.
