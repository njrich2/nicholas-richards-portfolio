# nba--analysis

**Abstract**:

 The NBA is shifting towards a positionless style of play, with players breaking away from traditional roles like PG, SG, SF, PF, and C. Centers are shooting more threes, Small Forwards are handling the ball, and taller Point Guards are emerging. Our goal is to model a player’s position based on their statistics and analyze the variance in positional probabilities to assess the relevance of traditional definitions. Finally, we propose a new “archetype” classification system to better reflect players' playing styles.

**Introduction**:

In 2017, an NBA executive said, “I don’t have the five positions anymore, it may be as simple as three positions now, where you’re either a ball-handler, a wing, or a big.” Our question is whether or not the traditional five positions of the NBA are an accurate descriptor of not only how teams construct themselves but also how players are defined in their roles. We then speculate about how this could potentially impact winning in the NBA. 

This could better help NBA organizations construct their teams by having a more accurate representation of what players’ roles are in the modern-day NBA. You would not put the same players around a 6'7 PG as you would a 6'2 PG or a C who stretches the floor and shoots 3s versus a C who sits in the paint and grabs rebounds. By classifying players by archetype rather than position, we introduce the possibility for more insightful roster construction. 

To create our archetypes we used KNN and K-Means Clustering using player statistics for our features. When trying to predict player positions based on their season statistics we used both a Random Forest and Gradient Boosted model. Players are typically selected based on their strengths, creating distinct roles within a team, and grouping player profiles can provide more reliable data when there are gaps in individual player information. However, some players may not fit into predefined roles, and shot percentage alone does not fully capture the complexity of shot selection.

Setup:

Our Dataset:

- Originally scraped data using the NBA_API
  - However we encountered issues in the classifications of these positions. The NBA_API has seven positions instead of five (Including a player’s primary position and secondary position e.g. Forward, Center-Forward, etc.) so we decided to pivot.
- Instead scraped from BasketballReference, a comprehensive online database and resource for basketball statistics
  - We scraped Player names, Position, Team, Age, Season, Average Distance of FGA, FGA% at different distances (0-3ft, 3-10ft, 10-16ft, and 16-3p), and many other on-court statistics

Experiment:

- Random Forest and Gradient Boosted model parameters:
We used all of the parameters in our dataset (excluding Player name, Season, and stats like that)
- K-Means Clustering parameters
FG% FT%, AvgDist, 2PA%, 3PA%, 2P%, 3P%, 0-3A%, 3-10A%, 10-16A%, 16-3PA%, DnkFGA%, Cnr3PA%', 3PA_PM, 2PA_PM, FTA_PM', ORB_PM, DRB_PM, AST_PM, STL_PM, BLK_PM, TOV_PM, PTS_PM


Random Forest & K-Means Clustering

- Both models have an accuracy of about 59%, which indicates that they are correctly predicting the player’s position about 59% of the time. This is relatively low for a classification task but it can be explained by the complexity of predicting a player’s position based on player statistics.

- The Macro Average for Precision is about 0.62 for both models, suggesting that both perform similarly in terms of overall balance across all player positions. For recall, it is 0.60 and for F1-Score it is 0.61, indicating a similar performance balancing precision and recall across all positions.

- Random Forest tends to confuse Power Forwards with Small Forwards. 
Gradient Boosting makes more mistakes when predicting Small Forwards and Shooting Guards. 

**Conclusion**:

- Our models were successful in supporting our hypothesis that the NBA is becoming less reliant on historic definitions of each position in the NBA and is moving towards a more “positionless” style of basketball

- This is further supported when we look at the breakdown of our archetypes by position, as each cluster has various positions within it, and one cluster doesn’t fully represent or describe one player, but rather a style or role of basketball played. 

- If we were to continue this project, we would be interested in weighting our parameters and introducing new features such as physical attributes (height, weight, vertical, strength, etc.) that could further describe a player's style of play and that were not available in our current dataset. 

- Based on our findings we would recommend NBA organizations to abandon their biases about how each position is supposed to play, and instead look at how different players play within their position to construct their teams.



