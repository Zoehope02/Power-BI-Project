# Power-BI-Project
Netflix TV Show &amp; Movie Analysis

## Objective 
This project aims to compare the performance of TV shows and movies, using customer satisfaction as the main metric. By analyzing ratings and votes, it evaluates how well different titles are performing. The dashboard also includes images and summaries of each show and movie, offering a comprehensive overview and insightful analysis of Netflix's performance.

## DAX Measures Created: 
``` 1. Movie Title
Movie Title = 
CALCULATE(
    COUNT(Listings[Listings Type]), 
    Listings[Listings Type] = "Movie"
)

2. Movie Votes
Movie Votes = 
CALCULATE(
    SUM(Listings[Votes]), 
    Listings[Type] = "Movie"
)

3. % Movie Titles
% Movie Titles = 
DIVIDE(
    CALCULATE(
        COUNTROWS(Listings), 
        Listings[Listings Type] = "Movie"
    ), 
    COUNTROWS(Listings), 
    0
)

4. % Movie Votes Label
% Movie Votes Label = 
VAR _percentoftotal = FORMAT(ROUND(DIVIDE([# Movie Votes],[# Votes], 0), 2) * 100, "0.00") 
VAR _votespertitle = FORMAT(ROUND(DIVIDE([# Movie Votes], [# Movie Title], 0), 0), "#,##0")
RETURN
"(" & _percentoftotal & "%) | " & _votespertitle & " votes per title"

5. Movie AVG Rating
Movie AVG Rating = 
CALCULATE(
    AVERAGE(Listings[Rating Group]), 
    Listings[Listings Type] = "Movie"
)```


        
