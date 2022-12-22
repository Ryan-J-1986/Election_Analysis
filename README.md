# Colorado Congressional Election Audit

## Overview of Election Audit
This audit was completed in order to process the tabulated results for the congressional election in Colorado. The audit analyzed the data in order to determine the total number of votes cast in the election and how they were spread out, both among the candidates on the ballot and the districts where voting was conducted. This information is important not only for determining the winner of the election, but also for understanding the turnout by number of voters across the three districts represented in the election.

## Election Audit Results
* 369,711 total ballots were cast in this election.

![Output showing total votes cast](/Resources/total_votes.png)

```
for row in reader:

        total_votes = total_votes + 1
```
* Jefferson County cast 10.5% of the total ballots cast, for a total of 38,855 ballots.
* Denver County cast 82.8% of the total ballots cast, for a total of 305,055 ballots, by far the largest turnout of the election by county.

![Output showing county with largest turnout](/Resources/largest_turnout.png)

* Arapahoe County cast 6.7% of the total ballots cast, for a total of 24,801 ballots.

![Output showing vote totals by county](/Resources/county_votes.png)

* Charles Casper Stockham received 23.0% of the total ballots cast, for a total of 85,213 ballots.
* Diana DeGette receieved 73.8% of the total ballots cast, for a total of 272,892 ballots.
* Raymon Anthony Doane received 3.1% of the total ballots cast, for a total of 11,606 ballots.

![Output showing vote split among candidates](/Resources/candidate_totals.png)

* The winner of the election is Diana DeGette, with a vote percentage of 73.8% and 272,892 ballots.

![Output showing winning candidate and their vote totals](/Resources/winning_candidate.png)

```
votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
...
if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
```

## Election Audit Summary

The script used in the audit for this election could be easily modified to provide a near-identical analysis to any single-choice voting election that can be won with a simple highest vote total. It would require the data storing the ballot information be formatted relatively similarly, but in order to modify the script to adapt to differences in formatting there are two variables that would need to be updated to align with the data set being analyzed. They are the variables that identify the location in the data of the candidate who was voted for, and the location in the data of the county of residence for the voter.
```
candidate_name = row[2]
county_name = row[1]
```
The creation of these two variables is used to loop through the data and identify the different values present in the data, which are then stored in lists that function as the core of the output for the audit.These variables are tallied while looping through the data and the vote totals associated with the variables are stored in dictionaries, all of which serves to determine the vote totals for each candidate and county and also determine the winner of the election.
```
candidate_options = []
county_list = []
...
for row in reader:
...
  if candidate_name not in candidate_options:
      candidate_options.append(candidate_name)
      candidate_votes[candidate_name] = 0
  candidate_votes[candidate_name] += 1
  ...
  if county_name not in county_list:
      county_list.append(county_name)
      county_votes_dict[county_name] = 0
  county_votes_dict[county_name] += 1
```
These variables are tallied while looping through the data and the vote totals associated with the variables are stored in dictionaries, all of which serves to determine the vote totals for each candidate and county and also determine the winner of the election. By simply updating the two variables to tell the script where to look in the data set for the candidate and the county names you could use this script and likely not require many other alterations in order to see results like the ones found in this audit.
