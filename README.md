# Reducing Stochastic Noise in Collegiate Basketball Analytics

## The Problem
Standard basketball metrics often fail to account for random variation due to shooting performance. In high-variance environments like NAIA basketball, the "true" performance of players, lineups, and teams is confounded by small sample size and random shooting streaks.

**Intuitive Example** Two lineups, A and B, might play 5 defensive possessions each. Imagine both lineups surrender the same exact shot on each possession: a wide-open, catch-and-shoot corner 3-pointer to the opposing team's shooting guard. However, against Lineup A, the opponent makes each of the shots. Against Lineup B, the opponent misses each of the shots. In this example, Lineup A and Lineup B performed the exact same. But traditional lineup evaluation metrics will punish Lineup A and reward Lineup B. My metric aims to address this discrepancy by evaluating "quality" of shot vs observable binary "result" of shot (make/miss).

## The Solution: Shot Quality
I derived a new metric that assesses the expected value of any basketball shot by determining its objective difficulty vs its point value. The metric is evaluated against several parameters, including shot location, defender positioning, shot type (e.g. off the dribble vs catch-and-shoot), and time remaining on the shot clock. By substituting in the sum of "shot expected values" for "points" in traditional basketball metrics, a more accurate idea of player, lineup, and team performance is achieved.

## Validation
I tested my metric with Kuder-Richardson Formula 20 using a modified variance calculation to assess metric stability:
$$KR_20 = \frac{N}{N-1} (1 - \frac{\sum_{i=1}^N p_i(1-p_i)}{\sigma^2})=0.910$$ 

**What this means:** Approximately 91% of the variance in shot quality reflects actual variance in the difficulty of the shots. Calculated KR-20 significantly exceeded standard threshold value of 0.7.  

## Applications
I applied the metric in a limited capacity in several facets of analytic work to demonstrate its capabilities to the coaching staff:
* **Player Evaluation:** EFG+ (effective field goal % adjusted with shot quality) was tested on a player's data from the 23-24 season
* **Lineup Evaluation:** OEff+ and DEff+ (offensive/defensive efficiency adjusted with shot quality) were tested on 5 heavily used lineups in a game from the 23-24 season
* **Team Evaluation:** PTP+ (total expected value of all shots + freethrows) was calculated for both teams in 3 games from the 23-24 season

## Methodology and Tools
* Analysis Platform: Microsoft Excel
* Statistical Approach: KR-20 to assess metric stability
* Data Source: Synergy Sports Platform
* Data Handling: Manual tracking of NAIA game film

## Repository Contents
* `analysis/`: Contains the Exel source file used to derive the metric along with KR-20 testing and basic applications.
* [📄 Shot Quality Research Paper (PDF)](paper/Shot-Quality-Research.pdf): The full research paper detailing the derivation and validation.
