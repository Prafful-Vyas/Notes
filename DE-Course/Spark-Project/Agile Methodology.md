If you are a developer, how do you get tasks to work on?

### Agile & Waterfall

big project - 6 months (entire thing)
Agile - Sprints (1 week / 2 week)
6 sprints (2 weeks)
12 weeks (3 months)

We develop the project incrementally
2 weeks something which can be demo is developed.

stories (not written in technical way)
	- can you impement logging for this project - 2 points
	- can you bring customers data to the data lake

As a developer you would be assigned a few stories
each story has story points

- 1 (in a few hours)
- 2 (1 day)
- 3 (2 days)
- 5 (3-4 days)

Initiative -> Epics -> Stories

![[Pasted image 20260217223404.png]]

### Story Example

Data Storage - Create a Data lake to store a raw, cleaned and processed data for future analysis.

Data Ingestion - Create a scheduled job to extract data from an external database and load it to our data lake

Data transformation - Create a data transformation pipeline to clean and standardize incoming customer data. Enrich the data with additional attributes.

Data Processing - Design and implement a batch pipeline to aggregate monthly sales data.

Realtime data - Create a realtime streaming pipeline for monitoring website traffic.

Data Quality & Validation - Implement automated data validation checks to ensure the integrity of incoming data.

Data Documentation - Document the data Schemas for the customer database to facilitate data analysis. Maintain up to date documentation for ETL processes.

Testing - write unit tests for data transformation functions to ensure that logic is correct.

Performance Optimization - fine tune the jobs to improve resource utilization and minimize processing time.

Deployment and Scaling - setup automated deployment pipelines for data processing jobs to streamline deployment to production. Design an auto scaling infra to handle increased data volumes during peak hours.


