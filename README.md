# nba-expected-bucket

Predicting the outcome of shots based on the events and tracking data available for the 2015/16 season.

## Quick links:

- [Exploratory Data Analysis](analysis/eda/Exploratory%20data%20analysis%20on%20shots%20data.ipynb)
- [ML Model](analysis/ml/ml.ipynb)

## Data

The repo combines events data and tracking data from the 2015/16 season.

### Data Source:

- Events data: NBA events and shots api
- Tracking data: https://github.com/linouk23/NBA-Player-Movements

### Features used in the model

#### Categorical Features

| SHOT_TYPE | SHOT_ZONE_BASIC       | SHOT_ZONE_AREA        | SHOT_ZONE_RANGE | ACTION_TYPE_SIMPLIFIED |
| --------- | --------------------- | --------------------- | --------------- | ---------------------- |
| 2PT       | Mid-Range             | Right Side Center(RC) | 16-24 ft.       | Layup                  |
| 3 PT      | Above the Break 3     | Right Side(R)         | 24+ ft.         | Dunk                   |
|           | Restricted Area       | Center(C)             | 8-16 ft.        | Hook Shot              |
|           | In The Paint (Non-RA) | Left Side(L)          | Less Than 8 ft. | Jump Shot              |
|           | Left Corner 3         | Left Side Center(LC)  |
|           | Right Corner 3        |

#### Numerical Features

| AVERAGE_DEFENDER_DISTANCE | SHOOTER_DEFENDER_DISTANCE | OFFENSE_SPACING | DEFENSE_SPACING | SHOT_CLOCK |
| ------------------------- | ------------------------- | --------------- | --------------- | ---------- |

#### Calculating Spacing

I used convex hull technique to calculate the `OFFENSE_SPACING` and `DEFENSE_SPACING`. This is explained much better here: http://projects.rajivshah.com/sportvu/Chull_NBA_SportVu.html

`AVERAGE_DEFENDER_DISTANCE` and `SHOOTER_DEFENDER_DISTANCE` are calculated using the [distance formula](https://en.wikipedia.org/wiki/Euclidean_distance).

## Where do teams take their shots from?

<img src="images/hexbin of all shots.png" alt="Hex bin of shots">

## Does better spacing result in higher shooting percentage?

From the charts below we can infer that, although that is not the case always, we do see that among the teams with shooting percentage higher than the league average, the spacing also is better and vice versa

<p display="flex">
    <img width="48%" src="images/average_defense_spacing vs field_goal_percentage.png" alt="average defense spacing vs field goal percentage">
    <img width="48%" src="images/average_offense_spacing vs field_goal_percentage.png" alt="average offense spacing vs field goal percentage">
</p>

<p display="flex">
    <img width="48%" src="images/average_defense_spacing vs two_point_percentage.png" alt="average defense spacing vs two point percentage">
    <img width="48%" src="images/average_offense_spacing vs two_point_percentage.png" alt="average offense spacing vs two point percentage">
</p>

<p display="flex">
    <img width="48%" src="images/average_defense_spacing vs three_point_percentage.png" alt="average defense spacing vs three point percentage">
    <img width="48%" src="images/average_offense_spacing vs three_point_percentage.png" alt="average offense spacing vs three point percentage">
</p>

## Shooting % based on zones?

<img src="images/Shooting percentage based on zones.jpg" alt="Shooting percentage based on zones">

## Points per shot based on zones?

<img src="images/Points per shot based on zones.jpg" alt="Points per shot based on zones">

## Performance of ML Models

### Decision Tree

<img src="images/Decision tree shooting percentage based on zones.png" alt="images/Decision tree shooting percentage based on zones">

<img src="images/Decision tree points per shot based on zones.png" alt="images/Decision tree points per shot based on zones">

### Random Forest

<img src="images/Random Forest shooting percentage based on zones.png" alt="images/Random Forest shooting percentage based on zones">

<img src="images/Random Forest points per shot based on zones.png" alt="images/Random Forest points per shot based on zones">

## LICENCE

[MIT](LICENCE)
