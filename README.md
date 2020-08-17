# Overview of Election Audit
## Purpose 
The purpose of this analysis is to assist Tom in the Colorado board election by generating a vote count report to certify the congressional race. This will be revealed by analyzing the election result dataset by using python to generate the total votes, total votes for each candidate, winner of the election based on popular vote, voter turnout for each county, percentage of votes from each county and per candidate out of the total count, and county with the highest turnout.  The audit consists of mail, punch, DRE, hand, machine, and computer votes which is all counted and saved to election results csv file. The election results dataset contains the ballot id, county, and candidate name.  Conclusions will be reported based on the analyses of the dataset and presented in a text file. The overall results based on the analyses of the congressional race there are a total of 369,711 votes. As for per county vote Jefferson had 10.5% (38,855) of the total votes, Denver had 82.8% (306,055) of the total votes, and Arapahoe had 6.7% (24,801) of the total votes. The largest county turnout was Denver.  Percentage of votes per candidate as follow: Charles Casper Stockham had 23.0% (85,213), Diana DeGette had 73.8% (272,892), and Raymon Anthony Doane had 3.1% (11,606).  The winner of the Colorado board election is Diana DeGette with the winning vote of 272,892 and a 73.8% of winning percentage. 







	
# Election-Audit Results

The final results of the election:

[Election Results](analysis/election_results.txt)

- How many votes were cast in this congressional election?
  - There were 369,711 votes in this congressional election. The code used to get this result:
  
```

with open(file_to_load) as election_data:
  reader = csv.reader(election_data)
  header = next(reader)
  for row in reader:
      total_votes = total_votes + 1

```

- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
  - Jefferson had 10.5% which had 38,855 votes, Denver had 82.8% which had 306,055 votes, and Arapahoe had 6.7% which had 24,801 votes. 
    These variables were set towards the beginning of the code:

 ```

candidate_options = []
candidate_votes = {}
county_options = []
county_votes = {}

```
   The code used to retrieve this result:
   

```
  for county_name in county_votes:
    countyvotes = county_votes.get(county_name)
    county_percentage = float(countyvotes) / float(total_votes) * 100
    county_results = (f”{county_name}: {county_percentage:.1f}% ({countyvotes:,})\n”)
    print(county_results)

```

- Which county had the largest number of votes?
  - The county with the largest number of votes was Denver. The code that was used to determine this:
  
```
if (county_votes > county_count): 
    county_count = countyvotes
    largest_county = county_name
```

- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
  - Charles Casper Stockham had 23.0% which was 85,213 votes, Diana DeGette had 73.8% which was 272,892 votes, and Raymon Anthony Doane had 3.1% which was 11,606     votes.  

    These variables were set towards the beginning of the code:
```
candidate_options = []
candidate_votes = {}

```

   The code that was used to collect this data:

```
for candidate_name in candidate_votes: 
	votes = candidate_votes.get(candidate_name)
	vote_percentage = float(votes) / float(total_votes) * 100
	candidate_results = (f”{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n)
	print(candidate_results)
  
```

- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
  - The winner of the election was Diana DeGette, with a total of 272,892 votes which is a 73.8% of the total votes.
     These variables were set towards the beginning of the code:
```
winning_candidate = “”
winning_count= 0 
winning_percentage = 0
```
   The code that used to retrieve the winner:
```
if (votes > winning_count) and (vote_percentage > winning_percentage):
	winning_count = votes
	winning_candidate = candidate_name
	winning_percentage = vote_percentage
```
# Election-Audit Summary

The first proposal is to modify the script to exhibit the runner ups in the final results; having first, second and third. The second proposal is to modify the script to add a representation of who within the county was voted for, the total votes per candidate within each county.


