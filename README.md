## Project Tasks Overview:

### Part 1: Concert seating proximity data anaylsis with Spark-RDDs:
Before performing any kind of analysis, 3 datasets had to be created using Python. The 3 datasets called PEOPLE-large, INFECTED-small and PEOPLE-SOME-INFECTED-large. Each line
(person) of those files was composed of x and y coordinates indicating their location, an ID which served as their unique identifier, a name, and an age. PEOPLE-large was a
large data file which contained every person who attended the concert. However, what we didn't know was who in this file (which people) were infected with COVID or not. 
INFECTED-small was a small subset of PEOPLE-large and had the exact same data schema as it plus an "Infected" attribute. However, everyone in the INFECTED-small file was 
infected with COVID. PEOPLE-SOME-INFECTED-large was the same dataset as PEOPLE-large except for the fact that that this dataset contained an additional column “Infected” 
which indicated whether a person was infected with COVID or not (“yes” or “no”) based on the records in the INFECTED-small file.

Once the data creation was all done, the following queries using Spark-RDD had to be performed.

Query 1 required us to find all people p-j in the PEOPLE-large file who were at risk of having become infected with COVID due to having been seated within 6 units range of 
infect-i for each infected person (infect-i) listed in the INFECTED-small file. We were required to return the list of join pairs composed of people pi from the 
PEOPLE-large files that were a close contact with the person infect-i that infected them in the format of (pi, infect-i). 

Query 2 required us to return the pi.id of all people pi from PEOPLE-Large that were a close contact to at least one infected person at the concert. If a person pi was close 
contact of two or more different infected people, that person pi only needed to be returned once. The result needed to be returned in the form of (pi.id).

Query 3 required us to count how many people p-j in the same file are within 6 feet range of infect-i for each infected person infect-i in the PEOPLE-SOME-INFECTED-large file 
while preventing people from counting themselves.

### Part 2: Customer item purchase transaction data analysis with SparkSQL:
Before performing any kind of analysis, 2 datasets had to be created. Those datasets were called Customers and Purchases. Each line in the
Customers file represented one customer, and each line in Purchases file represented one purchase transaction.
Each person in the Customer dataset had the following attributes
ID: unique sequential integer from 1 to 50,000
Name: random sequence of characters of length between 10 and 20
Age: random integer between 18 to 100
CountryCode: random integer between 1 and 500
Salary: random float between 100 and 10,000,000
Each line in the Purchases dataset had the following attributes for each purchase transaction:
TransID: unique sequential integer from 1 to 5,000,000 
CustID: References one of the customer IDs, i.e., on Avg. a customer has 100 transactions.
TransTotal: Purchase amount as random float between 10 and 2000
TransNumItems: Number of items as random integer between 1 and 15
TransDesc: Text of characters of length between 20 and 50

Once the data creation was all done, the following queries using SparkSQL had to be performed.

Query 1 required us to filter out the purchases from the Purchases dataset with a total purchase amount above $600. We then had to store the result in a T1 csv file.

Query 2 required us to group the Purchases in T1 by the Number of Items purchased. For each group, we had to calculate the median, min and max of total amount spent for 
purchases in that group, and report the result directly on the console.

Query 3 required us the Purchases in T1 by customer ID only for young customers between 18 and 25 years of age. For each group, we had to report the customer ID, their age, 
and total number of items that this person has purchased, and total amount spent by the customer. We then had to tore the result as T3 csv file.

### Part 3: Forecast total item purchase amounts with MLlib:

For this part of the project, we were required to use the same datasets we created in Part 2.

The first task of this part required us to generate a subset of the dataset composed of customer ID, TransID, Age, Salary, TransNumItems and TransTotal, and refer it as
"dataset". We then had to randomly split the "dataset" into two a training set and testing such that the training set contains 80% of the "dataset" and the testing the remaining 20%.

The second task of this part, we had to make 2 regression models in which the "features" (X) for this task are Age, Salary, TransNumItems and the "outcome" (Y) is TransTotal. 
After doing so, we were required to train the models over the training set made during the previous task and applied over the testing set made during the previous task.

