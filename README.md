# The Jungle
DSC80 Project 4

## Introduction

*The League of Legends dataset contains game information from pro League games in 2022. The question I seek to answer is this: Can we effectively predict the outcome of a match based on the Jungler's performance? This question is highly relevant to League of Legends in its current state: the jungle role has been repeatedly toned down by the developers, reaching a point where many players complain that the role feels underpowered, that junglers have much less impact on the game then they ought to, given the difficulty of the role. Despite these sentiments from many players, others argue that jungle is still a dominant role, which, by the very nature of not being confined to one area of the map (like every othe role), is inherently powerful and not in need of any tune ups from the developers. As League of Legends is an significnalty complicated game, answering this question with data offers much more promise of finding a convincing answer than the raging debates online.<br><br>The dataset I will use to answer this question has 148,992 rows, with groups of 12 rows corresponding to individual games, meaning the dataset convers 12,416 pro games from 2022. The columns of interest for my analysis are as follows: result (outcome of the game), kills (number of enemies slaim by the jungler), assists (number of enemies the jungler assisted in slaying, not counting their own kills), deaths (number of times the jungler died), dragons (number of dragons the team slew), heralds (number of rift heralds the team slew), firstbaron (whether the team slew the Baron Nashor first), and earned gpm (amount of gold the jungler earned per minute). Kills, assists, deaths, and gold per minute are all standard assessments of a player's performance in the game, regardless of role. Dragons, Heralds, and Baron Nashor are known as 'Epic Monsters', and provide a powerful teamwide boost when slain. Securing the kill on these monsters is one of the jungler's main jobs, and a good measure of their performance.*

## Data Cleaning and Exploratory Data Analysis

*To clean the data, I first isolated relevant columns for my analsyis. All columns mentioned above were included, along with several more that did not end up being used in the final model, such as vision score (a measure of how much a player contributed to gaining vision of obsured areas of the map) and total cs (a measure of how many minions and monsters a player slew, highly correlated with their gold per minute). I then imputed 0's for missing by design columns, specifically those columns pretaining to first blood, as a NaN simply means the player did not get the first kill in the game. Next, certain information such as dragons slain was only stored in two rows pertaining to each team in the game, so I merged these rows with the rows corresponding to individual players, so that all the relavent information is stored in one row. Next, I isolated the rows corresponding to junglers, as no other role's information is needed for the analysis. The resulting cleaned dataframe's head is presented below:<br><br><br>| gameid                  | teamid                          | position | gamelength | result | kills | assists | deaths | firstbloodkill | firstbloodassist | firstbloodvictim | firstdragon | dragons | firstherald | heralds | firstbaron | barons | visionscore | earned gpm | total cs |
|-------------------------|---------------------------------|----------|------------|--------|-------|---------|--------|----------------|------------------|------------------|-------------|---------|-------------|---------|------------|--------|-------------|------------|----------|
| ESPORTSTMNT01_2690210   | oe:team:68911b3329146587617ab2973106e23 | jng      | 1713       | 0      | 2     | 6       | 5      | 0.0            | 1.0              | 0.0              | 0.0         | 1.0     | 1.0         | 2.0     | 0.0        | 0.0    | 48.0        | 188.0210   | 148.0    |
| ESPORTSTMNT01_2690210   | oe:team:d2dc3681437e2beb2bb4742477108ff | jng      | 1713       | 1      | 4     | 10      | 1      | 0.0            | 0.0              | 0.0              | 1.0         | 3.0     | 0.0         | 0.0     | 0.0        | 0.0    | 39.0        | 228.4764   | 183.0    |
| ESPORTSTMNT01_2690219   | oe:team:6dcacec00a6ba7576c5ab7f30c995cd | jng      | 2114       | 0      | 1     | 1       | 2      | 0.0            | 0.0              | 0.0              | 0.0         | 1.0     | 1.0         | 1.0     | 0.0        | 0.0    | 52.0        | 174.3803   | 215.0    |
| ESPORTSTMNT01_2690219   | oe:team:5380cdbc2ad2b8082624f48f99f6672 | jng      | 2114       | 1      | 6     | 7       | 0      | 1.0            | 0.0              | 0.0              | 1.0         | 4.0     | 0.0         | 1.0     | 1.0        | 2.0    | 62.0        | 286.5752   | 253.0    |
| 8401-8401_game_1        | oe:team:f4c4528c6981e104a11ea7548630c23 | jng      | 1365       | 1      | 0     | 13      | 1      | 0.0            | 0.0              | 0.0              | NaN         | 2.0     | NaN         | NaN     | NaN        | 1.0    | 39.0        | 262.9011   | 145.0    |
| 8401-8401_game_1        | oe:team:df80f468a3f9a722df056fe9104f052 | jng      | 1365       | 0      | 1     | 2       | 3      | 0.0            | 0.0              | 0.0              | NaN         | 1.0     | NaN         | NaN     | NaN        | 0.0    | 35.0        | 163.8681   | 120.0    |
*

## Assessment of Missingness

*Discuss your assessment of missingness in the data. Include any specific columns analyzed for missingness, the types of missingness identified, and how you addressed them.*

## Hypothesis Testing

*Detail the hypothesis testing performed, including the null and alternative hypotheses, test statistics used, and conclusions drawn from the tests.*

## Framing a Prediction Problem

*Explain how you framed the prediction problem, including the response variable chosen and the type of model (classification or regression). Describe why this problem is important and relevant to the project.*

## Baseline Model

*Outline the baseline model you created, including the features used and the model's performance. Explain why this model was chosen as the baseline.*

## Final Model

*Describe the final model, including any additional features engineered, model improvements made, and the final model's performance. Highlight how the final model improves upon the baseline model.*

## Fairness Analysis

*Present the fairness analysis conducted for the final model. Describe the groups compared, the evaluation metric used, and the outcomes of the fairness assessment. Include any findings on whether the model performs fairly across different groups.*

