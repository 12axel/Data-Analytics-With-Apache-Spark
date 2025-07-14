## Project Tasks Overview:
# Part 1: Concert seating proximity data anaylsis with Spark-RDDs:
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


