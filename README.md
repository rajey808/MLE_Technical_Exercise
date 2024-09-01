# Title : Advanced Analytics MLE Technical Exercise <br>
## Author : Yash Raje <br>
Notes : Please see the notebook for the code

# Question 1 <br>
Anwser <br> 
Industry : Retail Trade <br>
Filled Jobs (avg) : 194,054

# Question 2 <br>
Answer <br>
Industry : Wholesale Trade <br>
Period : 2023.03 <br> Operating Income Sales : 38,810

# Question 3 <br>
Assumption : Excluding 'Filled jobs (workplace location based)' <br>
Answer <br>
Territory : Auckland <br>
Cumulative Jobs Filled : 34,995,011 

# Question 4
The specific methodology is dependent on the tool or pipeline but the concepts remain the same.
Data warehousing tools (such as Snowflake) can help support auditing inputs. 

A feedback loop using a DataOps monitoring process could be used to monitor and improve a pipeline over time.
One way this can be done is to pick up abnormalities (e.g. wrong data type, null or missing data) in the data and raise an alert.
Another step in the process could also track the dataset sizes (e.g. row count) over time to check for consistent sizes in input data. 
E.g. if an input file has hourly KPI values for the past day, it is expected to have a consistent number of rows over time, any inconsistency can be flagged.

For duplicates, a common usage in SQL is the "DISTINCT" keyword with the column names to retrieve only unique values.

There are many methods we can use to check for incorrect datatypes. One such is the regex matching the incoming values in a field.
Depending on the tool, there are type cast checking functions, e.g isNumeric function which can be used for this purpose.

For missing date rows you can use mean imputation taking the other datetime values into account. 
I have used this method in my time series clustering dataset to add in missing datetime rows as each trend needed the same number of data points for the function to work.

Similarly for null or missing values in a row, we can also use imputation (mean, 0 or any value imputation), or alternatively remove the entire row from the dataset.

# Question 5
BNZ provides a range of products to their customers, including loan and finance products for its business customers. <br>
I wanted to use a dataset which could provide useful insights to BNZ relating to the above. <br>

After looking through the data, I decided to use the employment dataset (job numbers by region) and an additional dataset from the Stats NZ website called the GDP by region dataset.<br>
My assumption and reasoning is that regions which have a higher Year-on-Year (YoY) growth rate for number of jobs filled provide an opportunity for BNZ to sell more financial loan products to new and growing businesses.<br>
The GDP growth data could help assess the risks of issuing these loans to businesses in the different regions, ie. regions with higher GDP growth could be seen as safer investments. <br>

I created a heatmap model to show the average YoY growth for GDP and average YoY growth for job numbers across regions in NZ.
Results and insights discussed below.

From the graph we can extract a couple of insights.<br>
All regions have a similar YoY GDP growth (mean of 8 with standard deviation of only 0.45).<br>
Though not all regions have a proportional increase in the YoY job numbers (mean of 2, but a much larger standard deviation of 0.83). <br> 
Supported by the summary statistics table above.<br>

We can see that the Tasman/Nelson region has the highest YoY job numbers growth amongst the regions while still having similar GDP growth suggesting there are increasing job numbers in that region so BNZ could focus on selling more business loans in that area.
The Northland region has a similar phenomenon.<br>
In contrast the West Coast region has low job numbers growth but still stable GDP growth suggesting there are fewer opportunities for BNZ to sell business loan products in that region.<br>
Due to the similar YoY GDP growth across most regions, loans in most regions can be thought of as being similarly safe.<br>

For improvements or further insights, I would suggest adding another variable to slice the data further.<br>
My thinking was creating a model for job numbers by industry and region, which could further help tailor buisness loans to specific industries.

