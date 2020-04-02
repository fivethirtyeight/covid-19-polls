# covid-19-polls

This repository contains the data behind [TKTK]()



## Polls

`covid_approval_polls.csv` contains polls that ask Americans whether or not they approve of the way Trump is handling covid-19.

`covid_concern_polls.csv` contain the polls ask Ameicans how concerned they feel about aspects of the outbreak such as infection and economic impact.

Column | Description
---------|-------------
`subject`| For approval polls, this column marks whose handling of covid-19 the approval poll is about (e.g. `Trump`). For concern polls, this column identifies which subject the poll is asking Americans about (for example, `concern-infected` vs `concern-economy`).
`modeldate`| Date of model run
`party`| Party of respondents
`startdate` | Start date of poll
`enddate`| End date of poll
`pollster` | Organization that conducted the polling
`grade` | Grade given to pollster in our [Pollster Ratings](https://projects.fivethirtyeight.com/pollster-ratings/)
`samplesize` | Size of polling sample
`population` | `A` for adults, `RV` for registered voters, `LV` for likely voters
`weight` | Weight given to each poll in the model 
`influence` | Weight given to each poll, adjusted for recency
`multiversions` | Multiple versions of the poll were averaged.
`tracking` | Polls with overlapping date samples.

## Averages

`covid_approval_toplines.csv` and `covid_concern_toplines.csv` contain the calculated daily averages for the approval and concern polls respectively.

Our averages are calculated similarly to how we handle [presidential approval ratings](https://projects.fivethirtyeight.com/trump-approval-ratings/), which means we [account for the quality of the pollster and each pollster’s house effects](https://fivethirtyeight.com/features/how-were-tracking-donald-trumps-approval-ratings/) (whether they seem to yield unusually high or low numbers for each question compared with the polling consensus), in addition to a poll’s recency and sample size. In cases where the pollster did not provide sample sizes by party, they were calculated based on the percentage of total respondents who identified with each party. If the same poll asked more than one relevant question (using different wording), we included both questions, but the results of those questions were averaged together, then input into the model, so the poll was not double counted.