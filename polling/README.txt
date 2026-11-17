Polling data: 2022 Cooperative Election Study (CES)
===================================================

Files
-----
voters.csv                 The dataset. One row per respondent, 22 columns.
ces22_common_pre_qx.pdf    The 2022 CES pre-election questionnaire. Question
                           names below (e.g. CC22_310a) refer to this document.
CES Guide 2022.pdf         The 2022 CES guide: sampling, weighting, and
                           response counts for every question.
media_consumption.csv      Older version of the dataset, kept for reference.
                           It has the same 60,000 rows in the same order and
                           17 of the 22 columns (all except pid7,
                           presvote20post, presvote16post, race and
                           gender4). Its values are identical to voters.csv.

voters.csv
----------
- 60,000 rows: the full 2022 CES Common Content sample. The response counts
  for each column match the counts in the CES Guide.
- Numeric codes are the response codes printed in square brackets in the
  questionnaire, e.g. "[1] Strongly approve".
- NA means the respondent skipped the question or was not asked it. The
  165 District of Columbia respondents were not asked about a state
  legislature or governor, so state_senate_control,
  state_lower_house_control, gov_party and approve_gov are NA for all of
  them.

Column-by-column mapping
------------------------
"Direct" means the column holds the questionnaire variable unchanged.
"Derived" means it was recoded from one or more questionnaire items, as
described.

Weights and demographics

  commonweight     Direct, but not a question. The CES survey weight for
                   all pre-election respondents, targeting the population
                   of US adults. It is described in the "Weighting" section
                   of the CES Guide, not in the questionnaire. Mean 1.
  birthyr          Direct. [birthyr] "In what year were you born?"
                   (1925-2004).
  gender4          Direct. [gender4] 1 Man, 2 Woman, 3 Non-binary,
                   4 Other.
  race             Direct. [race] 1 White, 2 Black or African-American,
                   3 Hispanic or Latino, 4 Asian or Asian-American,
                   5 Native American, 6 Two or more races, 7 Other,
                   8 Middle Eastern.
  state            Derived (labels only). [inputstate] "What is your State
                   of Residence?" The numeric code is replaced by the state
                   name. Includes District of Columbia (51 values).

Party identification and past vote

  pid7             Direct. [pid7] 7-point party ID: 1 Strong Democrat,
                   2 Not very strong Democrat, 3 Lean Democrat,
                   4 Independent, 5 Lean Republican, 6 Not very strong
                   Republican, 7 Strong Republican, 8 Not sure. (Code 9,
                   "Don't know", is never used.)
  party            Derived (labels only). The same variable as pid7, with
                   the codes replaced by the response wording printed in the
                   questionnaire. Note that this wording comes from the
                   follow-up question for people who did not pick a party,
                   so:
                     "The Democratic Party"   = pid7 3 (Lean Democrat)
                     "The Republican Party"   = pid7 5 (Lean Republican)
                     "Neither"                = pid7 4 (Independent)
                   pid7 and party agree on every row.
  presvote20post   Direct. [presvote20post] 2020 presidential vote:
                   1 Joe Biden, 2 Donald Trump, 3 Jo Jorgensen,
                   4 Howie Hawkins, 5 Other, 6 Did not vote for President.
  presvote16post   Direct. [presvote16post] 2016 presidential vote:
                   1 Hillary Clinton, 2 Donald Trump, 3 Gary Johnson,
                   4 Jill Stein, 5 Evan McMullin, 6 Other, 7 Did not vote
                   for President.

Political knowledge (all derived, coded "Correct" / "Incorrect" / "Not sure")

  house_control    From [CC22_310a] "Which party has a majority of seats
                   in the ... U.S. House of Representatives?"
                   (1 Republicans, 2 Democrats, 3 Neither, 4 Not sure).
                   At the time of the survey (fall 2022) Democrats held the
                   House: Democrats -> Correct; Republicans or Neither ->
                   Incorrect; Not sure -> Not sure.
  senate_control   From [CC22_310b], the same question about the U.S.
                   Senate, coded the same way (Democrats = Correct).
  state_senate_control
                   From [CC22_310c], the same question about the
                   respondent's state senate. "Correct" depends on which
                   party controlled that state's senate, so it varies by
                   state. Not sure stays Not sure.
  state_lower_house_control
                   From [CC22_310d], the same question about the
                   respondent's state lower chamber, coded the same way as
                   state_senate_control.
  gov_party        From [CC22_311a] "Please indicate whether you've heard
                   of this person and if so which party he or she is
                   affiliated with", asked about the respondent's governor
                   (1 Never heard of person, 2 Republican, 3 Democrat,
                   4 Other party / Independent, 5 Not sure). Naming the
                   governor's actual party -> Correct; naming the other
                   major party -> Incorrect. "Never heard of person",
                   "Other party / Independent" and "Not sure" are all
                   coded Not sure (the counts work out exactly this way).

Media use in the past 24 hours (derived from one check-all-that-apply item)

  [CC22_300] "In the past 24 hours have you... (check all that apply)".
  Each option becomes its own column, coded 1 = selected, 2 = not selected
  (the CES convention for multiple-selection items):
  social_media     Option [1] Used social media (such as Facebook or
                   Youtube).
  tv               Option [2] Watched TV news.
  newspaper        Option [3] Read a newspaper in print or online.
  radio            Option [4] Listened to a radio news program or talk
                   radio.
  Option [5] "None of these" is not included. The follow-ups CC22_300a
  (local vs national TV news) and CC22_300c (print vs online newspaper)
  are not included.

Job approval

  [CC22_320grid] "Do you approve of the way each is doing their job?"
  1 Strongly approve, 2 Somewhat approve, 3 Somewhat disapprove,
  4 Strongly disapprove, 5 Not sure. All four columns are direct copies,
  renamed:
  approve_pres     [CC22_320a] President Biden.
  approve_congress [CC22_320b] The U.S. Congress.
  approve_sc       [CC22_320c] The U.S. Supreme Court.
  approve_gov      [CC22_320d] The Governor of the respondent's state.

Source
------
Schaffner, B., Ansolabehere, S., and Shih, M. (2023). Cooperative Election
Study Common Content, 2022. Harvard Dataverse.
https://doi.org/10.7910/DVN/PR4L8P

The script that originally produced these files has been lost. The mapping
above was reconstructed by comparing voters.csv with the questionnaire and
with the response counts in the CES Guide.
