# Airlines Data Analysis Using Python

## Project Overview ##
Our hypothetical Airline company wants to analyze why their **Ticket Sales** are decreasing and why people are giving bad reviews and ratings to their airline. We have data for several Airlines, including **AirIndia**, **Indigo**, **Spicejet**, **Go First**, **Air India Express**, **AirAsia India**, **Vistara**. The goal is to understand how happy or unhappy their customers are. By analyzing customer reviews and ratings, we can identify what’s working well and where improvements are needed, helping to keep their customers happy and loyal.

## Data Source - [Indian Airlines Customer Reviews](https://www.kaggle.com/datasets/jagathratchakan/indian-airlines-customer-reviews)

## Python Libraries Used ##
Pandas, Matplotlib, Seaborn

## Problem Statements to Analyse Our Data ##

1. Analyze customer ratings to find out how many gave 1 star, 2 stars, and so on. Use a graph to show the distribution of ratings to easily identify whether most customers are happy or unhappy.
2. Organize the reviews by date to observe if the ratings have improved or worsened over time.
3. Compare how many customers would recommend the airline versus those who wouldn’t.
4. Identify the overall distribution of reviews for the airlines, whether they are mostly "Poor," "Good," or "Excellent."
5. Examine each airline’s reviews to determine the specific type of feedback they are receiving.


## Exlporatory Data Analysis ##
1. Imported Pandas, Matplolib, and Seaborn Libraries and the csv file into Jupyter Notebook using `pd.read_csv("Filename")`
<img width="961" alt="Imported Data" src="https://github.com/user-attachments/assets/47d58cce-14e0-455a-8316-ab9b4e2d89cb">

2. Exploring our dataset with `info` & `describe` function to get more idea about our data.
<img width="961" alt="Checking Data" src="https://github.com/user-attachments/assets/28fd8475-4edd-4bed-9873-5ccd516ec2c6">

3. Checking Null Values Available in the Dataset & handle them using Dropna method
<img width="1202" alt="Missing values" src="https://github.com/user-attachments/assets/3ec1df51-bcb9-4904-aaa3-70993952993e">

4. Creating a new column `[Recommend]` to from existing column `[Recommond]`
<img width="961" alt="Renaming column" src="https://github.com/user-attachments/assets/941e6dcf-96e2-4a32-80a0-42e8b08eec96">

5. Deleting the column `[Recommond]`
<img width="961" alt="Deleting column" src="https://github.com/user-attachments/assets/8996967d-2b4f-4801-a33f-3a3118904d73">

6. Renaming column name from `Rating - 10` to `Rating`
<img width="961" alt="Rename column" src="https://github.com/user-attachments/assets/41d8f8f6-0c78-4bd1-9976-6511cd51d77d">

7. Changing the Date Format to YYYY-MM-DD
<img width="961" alt="Date Format Change" src="https://github.com/user-attachments/assets/31019dfb-0481-409f-9e01-5922fe50892c">

## Solving Problem Statements with Charts & Visualisation ##

1. Look at the customer ratings and find out how many gave 1 star, 2 stars, and so on.

`a=sns.countplot(data=df, x=df['Rating'], color='dodgerblue') for i in a.containers: a.bar_label(i)`

<img width="761" alt="Ratings" src="https://github.com/user-attachments/assets/92055d4d-c2fd-46aa-a338-7dd31892d791">

_Note: Airlines received **986** ratings with **1 Star**, which is the highest, followed by **303** ratings with **10 Stars**._  

2. Organize the reviews by date and check if the ratings are getting better or worse over time.

`plt.figure(figsize=(10,7))
x=sns.countplot(data=df,x=df['Date'].dt.year, color="Orange", hue='Recommend')
    for i in x.containers:
        x.bar_label(i)
plt.title("Year Wise Reviews")`

<img width="961" alt="Year Wise Reviews" src="https://github.com/user-attachments/assets/5e882e2d-0fd2-4c87-8598-eee30848c8c4">

_Note: Over the years, there has been a noticeable increase in the number of reviews. While more customers are sharing their feedback, the majority are not recommending the services, which is a point of concern._

3. Check how many customers said they would recommend the airline, versus those who wouldn’t.

`y=sns.countplot(data=df, x=df['Recommend'], color="lightgreen")
for i in y.containers:
    y.bar_label(i)
plt.title("Customers Recommendation Status")
plt.xlabel("Recommendation")`

<img width="868" alt="Customer Recommendation" src="https://github.com/user-attachments/assets/88194d4d-7eb4-46aa-8a93-2a24c181c74a">

_Note: The customer recommendation bar graph shows that **1,444** people had a bad experience and do **not recommend** the airline, while **762** customers are satisfied with the service and do recommend it. We need to further investigate why so many customers had negative experiences._

4. Identify the overall distribution of reviews for the airlines, whether they are mostly "Poor," "Good," or "Excellent."

`plt.figure(figsize=(7,5))
plt.pie(reviews, labels=reviews.index, autopct="%0.1f%%")
plt.title("Customer Reviews Segmentation")`

<img width="724" alt="Reviews segmentation" src="https://github.com/user-attachments/assets/5ec627aa-6740-4865-b264-8b021be5dd82">

_Note: The pie chart reveals that a significant portion of customers are dissatisfied with their airline experience, with **55.3%** giving **Poor Reviews**, while only **21.3%** provided **Excellent** reviews._

5. Examine the reviews for each airline to determine the specific type of feedback they are receiving.

`plt.figure(figsize=(9,6))
an=sns.countplot(data=df, x=df['AirLine_Name'], hue='Reviews')
for i in an.containers:
    an.bar_label(i)`

<img width="946" alt="Airline Reviews" src="https://github.com/user-attachments/assets/c169ce25-e8df-4579-a950-4b1cf5da8496">

_Note: **Air India** has the highest number of poor reviews (**380**), followed by **SpiceJet** with **316**. Only **Vistara** stands out with a higher number of **Excellent** reviews compared to the other airlines._

## Final Recommendation ##
As we have seen, most of the reviews are poor, so to analyze this, I dug deeper into the reviews section. I grouped the "Customer Reviews" for each airline by their "Title." You can see the example in the image below.

<img width="961" alt="reviews grouping" src="https://github.com/user-attachments/assets/5bfed80e-1071-4adc-a003-89827d6860e2">

I performed this analysis for every airline, which helped me identify the exact reasons behind the negative feedback and pinpoint areas where we need to improve the airline services.

_**SpiceJet**:_  
_The majority of customers had a bad experience due to flight delays and poor customer service_

_**Vistara**:_  
_Customers reported negative experiences due to refund policies, poor customer service, and luggage handling issues_
_Customers were disappointed with poor customer service_

_**AirAsia India**:_   
_Almost all customers reported poor customer service_  
_Customers expressed dissatisfaction with service quality and frequent flight delays_

_**Go First Airlines**:_  
_Customers had a bad experience due to poor customer service and a lack of communication_  
_A major reason for the poor experience is frequent "Flight Cancellations"_  
_Many customers reported that the airline failed to update them properly, which led to negative reviews_

_**Indigo**:_  
_Flight Delays and Poor Time Management_  
_Rude and Unprofessional Staff_  
_Extra Charges and Baggage Issues_

_**Air India Express**:_
_Frequent Flight Delays and Poor Communication_  
_Rude and Unprofessional Staff_  
_Refund and Extra Charges Issues_

_**AirIndia**_  
_Terrible Customer Service_  
_Old and Unmaintained Aircraft_  
_Flight Delays and Poor Management_

_By addressing these issues, we can enhance customer experience, convert negative ratings into positive ones, and ultimately boost ticket sales for each Airlines._
