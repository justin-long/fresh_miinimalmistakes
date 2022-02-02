---
Title: "Simulating Major League Baseball Games"
excerpt: "Constructing an algorithim in SAS to simulate a Major League Baseball game utililizing Markov Chains. "
---
# Presentations
This project was presented at the following conferences.

 - Simulating Major League Baseball Games, INFORMS 2018, Phoenix AZ.  
- Simulating Major League Baseball Games, SAS Global Forum 2018, Denver CO.
- Simulating Major League Baseball Games,IFORS 2017, Québec City, Canada.

This research is also published in the SAS Global Forum 2018 proceedings available at [this link.](https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2018/2875-2018.pdf)

## Background
The game of baseball can be explained as a Markov Process, as each state is independent of all states except the one immediately prior. Probabilities are calculated from historical data on every state transition from 2011 to 2016 for Major League Baseball games and are then grouped to account for home-field advantage, offensive player ability, and pitcher performance. Using the probabilities, transition matrices are developed and then used to simulate a game play-by-play. For a specific game, the results give the probability of a win as well as expected runs for each team.

## Brief Methodology
Some simplifying assumptions were made, such as:

 - The starting lineup remains constant
 - No runs scored on 3rd out
 - 4 pitchers per team at a maxiumum
 - No events occurt in-between at-bats (e.g. steals, pickoffs, etc.)

Viewed as a Markov chain, baseball is a series of transitions from one state to another. In general, there are a total of eight base-states from which players move in and out. In order to account for runs and outs, the 8 possible base states are combined with having either 0, 1, 2, or 3 outs. This combination results in 32 base-out states. With these new states, runs can be inferred by certain transitions in the matrix. For example, a transition from state 3 with 0 outs to state 0 with 0 outs will yield 3 runs for the team. 

To represent state transitions easily, a 32x32 matrix is created, with rows and columns representing start and end states, respectively. Each cell of the matrix contains the probability of the transition from a start state to end state. Given a start and end state, probabilities are found by taking the number specific transitions and dividing by the total number of transitions to any end state. The transition matrix considers the number of outs that occurred on the play, so the number of runs that occurred on the play can then be derived. The number of runs that occur on each state transition are stored in a runs matrix, which is used in the simulation to determine the number of runs scored by each team.

To factor in a player’s offensive ability, weighted on base average (wOBA) is used. This measure gives a unique weight to all possible batting outcomes, and combines them into one statistic for a measurement of a player's overall offensive contribution. Once each player's wOBA is computed, they are grouped into one of 8 separate classes with the first class being the lowest performing players and class 8 being the best. Pitchers were classed in a similar manner. Skill-Interactive ERA (SIERA) was used to classify pitchers into one of 7 classes. SIERA estimates ERA through a pitcher's walk rate, strikeout rate, and groundball rate. It attempts to eliminate factors that aren't controlled by the pitcher.

Following classification of the pitchers, scalar matrices are developed by first creating 7 transition matrices based off a pitchers SIERA. The matrices are then compared to a league average matrix to create the scalar matrix which is applied to a batter’s transition matrix.

## Simulation Process

To calculate the winning percentage of a team, simulations are performed in SAS. The steps are as follow:


1. Select home and away teams

2. Set starting line-up for each team

3. Choose number of games to be simulated

4. Set starting inning and score

5. Begin inning in state 0 with 0 outs

6. Game iterates play-by-play

7. Runs are recorded for certain transitions

8. Batting team changes when a 3rd out state is reached

9. If there is not a tie, the game ends at the end of 9th inning

10. Win is recorded for the respective team

At the start of an inning, the first batter's transition matrix is used to select the next state of the game. The next batter in the lineup will start in the previous end state and so on for the rest of the batters. In the case of a tie at the end of the ninth inning, the simulation will continue to run until either team is winning at the end of one of the additional innings. The game will also end if the home team is winning after the away team bats in the ninth inning. The simulation also records the difference between the home team and away team’s score at the end of each game, and returns the average difference along with each team's win probability.

## Validation
For model validation, 10,000 simulations were constructed for the first half of the Cleveland Indains 2017 season. Thus, 81 games were simulated overall. On a game-by-game basis, our method was 65% accurate, whereas if only the number of wins was of concern, the algothihm was 89% accurate. 

## Further details
Please view the publication at [this link.](https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2018/2875-2018.pdf)

## Contributing Members
Brad Schweitzer, Warren Geither, and Sarah Roudybush also had contributing roles in this research. Dr. Christy Crute served as an advisor. 