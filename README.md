# covid-19-polls

This repository contains the data behind [How Concerned Are Americans About The Coronavirus?](http://projects.fivethirtyeight.com/coronavirus-polls/)



## Polls

`covid_approval_polls.csv` contains polls that ask Americans whether or not they approve of the way Trump is handling covid-19.

`covid_concern_polls.csv` contain the polls ask Ameicans how concerned they feel about aspects of the outbreak such as infection and economic impact.

Column | Description
---------|-------------
`subject`| For approval polls, this column marks whose handling of covid-19 the approval poll is about (e.g. `Trump`). For concern polls, this column identifies which subject the poll is asking Americans about (for example, `concern-infected` vs `concern-economy`)
`party`| Party of respondents
`startdate` | Start date of poll
`enddate`| End date of poll
`pollster` | Organization that conducted the poll
`sponsor` | Organization that sponsored the poll
`samplesize` | Size of polling sample
`population` | `A` for adults, `RV` for registered voters, `LV` for likely voters
`tracking` | `TRUE` if the poll is a tracking poll, meaning that the pollster is releasing data with overlapping samples
`text` | Text of the question the pollster asked
`url` | Link to the poll

### Adjusted Polls

`covid_approval_polls_adjusted.csv` and `covid_concern_polls_adjusted.csv` contain the polls after adjustments are applied by our poll-averaging algorithm. Additional columns include:

Column | Description
---------|-------------
`modeldate`| Date of model run
`grade` | Grade given to the pollster in our [Pollster Ratings](https://projects.fivethirtyeight.com/pollster-ratings/)
`weight` | Weight given to each poll in the model 
`influence` | Weight given to each poll, adjusted for recency
`multiversions` | `*` denotes that multiple versions of a poll in the raw data file were combined (see note below)

## Averages

`covid_approval_toplines.csv` and `covid_concern_toplines.csv` contain the calculated daily averages for the approval and concern polls respectively.

Our averages are calculated similarly to how we handle [presidential approval ratings](https://projects.fivethirtyeight.com/trump-approval-ratings/), which means we [account for the quality of the pollster and each pollster’s house effects](https://fivethirtyeight.com/features/how-were-tracking-donald-trumps-approval-ratings/) (whether they seem to yield unusually high or low numbers for each question compared with the polling consensus), in addition to a poll’s recency and sample size. In cases where the pollster did not provide sample sizes by party, they were calculated based on the percentage of total respondents who identified with each party.

If the same poll asked more than one relevant question (using different wording), we included both questions, but the results of those questions were averaged together, then input into the model, so the poll was not double counted.
