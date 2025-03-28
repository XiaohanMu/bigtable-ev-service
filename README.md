Assignment 3: Big Data Management with Google Cloud Bigtable

 

Due: Tuesday, 15th April 2025, at Midnight (11:59 PM CST)

The purpose of this assignment is to acquaint with Google Cloud Bigtable, a NoSQL database optimized for large-scale data storage and retrieval. You will work with real-world electric vehicle registration data, deploy a cloud-based database system, and implement API endpoints for querying data efficiently.

Programming Exercise: Introduction to Google Cloud Bigtable

 

This programming assignment can be tested using our autograder at any point. Simply go to the autograder website we have provided you and enter the URL of the Git repository you have created for this assignment.

 

Dataset: Electric Vehicle (EV) Population in Washington.

Link to dataset - Electric_Vehicle_Population_Data.csv Download Electric_Vehicle_Population_Data.csv                                                                                                                  

Sample Size: 100,000+ EV records                  

Some Attributes:

DOL Vehicle ID: Unique vehicle ID

County: County of the purchased EV

City: City of purchased EV

Make: Car manufacturer (BMW , Tesla)

Model Year: Year the vehicle was manufactured

Electric Range: Estimated electric driving range (miles)

 

Part 1: Setting Up a Google Cloud VM

Create a simple VM instance on gcp just like you created for HW2.

Important Note- When creating your Instance

Click Create an Instance
Scroll down to Security and Enable “Allow full access to all Cloud APIs”
 

Part 2: Setting Up Big Table (gcp)

Install all the dependencies
Enable Cloud Bigtable API:
Run in your SSH –

      gcloud services enable bigtable.googleapis.com

Create a Bigtable Instance named ev-bigtable
Run in your SSH –

     gcloud bigtable tables create ev-population \

  --instance=ev-bigtable \

  --column-families=ev_info

Create a table ev-population with following structure –
Column Family: ev_info
Row Key: DOL Vehicle ID
Columns: make , model , model year, electric range, city, county
Part 3: Loading Dataset into Bigtable

Download the dataset provided to you
Using a python script load the dataset into the table you created in part 2
Part 4: Querying

For this part you will be creating five endpoints using flask framework of python

/rows: that returns the total number of entries in Bigtable
/Best-BMW: Find the count of BMW EVs with an electric range > 100 miles
/tesla-owners: Retrieve the count of all Tesla vehicles registered in Seattle
/update: Update the electric range of the vehicle with DOL Vehicle ID 257246118 to 200 miles. 
/delete: Delete all records where the model year is less than 2014 and retrieve the count of remaining records. 
Important Note -

For /rows, /Best-BMW, /tesla-owners, and /delete:

Return just the number — not a JSON object or string-wrapped value.
Example (correct): return str(count)
Avoid (incorrect): return jsonify({'count': count}) or return f"Count is {count}"
For /update:

Return the literal string "Success" with quotes.
Example: return "Success"
We will check the code. Do not hardcode the solutions.

Submission Instructions:

Each individual must create a private GitHub repository and add the instructor/grader as a collaborator. The repository should contain the following three files:

Team.txt – A text file containing the Net ID.
HW3.txt – A text file containing the External IP of the Google Cloud VM instance.
Code.txt – A text file containing all Python scripts used in the assignment, including:
The script for loading data into Bigtable
The script for querying, updating, and deleting records
Submit Your GitHub link on Canvas.

Be sure to run our autograder at least once, as described above. This will upload the address of your repository and allow us to calculate the score for your programming assignment.

 

Autograder link -  http://34.69.37.230:8080Links to an external site.
