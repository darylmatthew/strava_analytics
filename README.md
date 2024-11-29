# Strava Analytics Project
Personal project that takes real Strava data from my own physical activities for data analysis.

Project Goals:
1. Visualise my own performance
2. Gather insights on training performance
3. Predict my marathon pacing based on my historical data
4. Find out when is the best time to train for me.
5. Find out the amount of rest I should have between sessions.
   
## Data Source:
Data collected from the offical Strava API, using my own account's physical activity data.

Thes are the initial columns and their respective data types:
| Column                        | Dtype     |
|-------------------------------|-----------|
| resource_state                | int64     |
| name                          | object    |
| distance                      | float64   |
| moving_time                   | int64     |
| elapsed_time                  | int64     |
| total_elevation_gain          | float64   |
| type                          | object    |
| sport_type                    | object    |
| workout_type                  | float64   |
| id                            | int64     |
| start_date                    | object    |
| start_date_local              | object    |
| timezone                      | object    |
| utc_offset                    | float64   |
| location_city                 | float64   |
| location_state                | float64   |
| location_country              | float64   |
| achievement_count             | int64     |
| kudos_count                   | int64     |
| comment_count                 | int64     |
| athlete_count                 | int64     |
| photo_count                   | int64     |
| trainer                       | bool      |
| commute                       | bool      |
| manual                        | bool      |
| private                       | bool      |
| visibility                    | object    |
| flagged                       | bool      |
| gear_id                       | object    |
| start_latlng                  | object    |
| end_latlng                    | object    |
| average_speed                 | float64   |
| max_speed                     | float64   |
| has_heartrate                 | bool      |
| heartrate_opt_out             | bool      |
| display_hide_heartrate_option | bool      |
| elev_high                     | float64   |
| elev_low                      | float64   |
| upload_id                     | int64     |
| upload_id_str                 | int64     |
| external_id                   | object    |
| from_accepted_tag             | bool      |
| pr_count                      | int64     |
| total_photo_count             | int64     |
| has_kudoed                    | bool      |
| athlete.id                    | int64     |
| athlete.resource_state        | int64     |
| map.id                        | object    |
| map.summary_polyline          | object    |
| map.resource_state            | int64     |


## Data Cleaning:
Looking at the dataset; I started the cleaning process by first, removing unimportant columns that were irrelevant to my analyses.

```sql
ALTER TABLE activities
DROP COLUMN name,
DROP COLUMN resource_state,
DROP COLUMN sport_type,
DROP COLUMN workout_type,
DROP COLUMN id,
DROP COLUMN timezone,
DROP COLUMN location_city,
DROP COLUMN location_state,
DROP COLUMN location_country,
DROP COLUMN kudos_count,
DROP COLUMN comment_count,
DROP COLUMN athlete_count,
DROP COLUMN photo_count,
DROP COLUMN trainer,
DROP COLUMN commute,
DROP COLUMN manual,
DROP COLUMN private,
DROP COLUMN visibility,
DROP COLUMN flagged,
DROP COLUMN gear_id,
DROP COLUMN start_latlng,
DROP COLUMN end_latlng,
DROP COLUMN has_heartrate,
DROP COLUMN heartrate_opt_out,
DROP COLUMN display_hide_heartrate_option,
DROP COLUMN upload_id,
DROP COLUMN upload_id_str,
DROP COLUMN external_id,
DROP COLUMN from_accepted_tag,
DROP COLUMN total_photo_count,
DROP COLUMN has_kudoed,
DROP COLUMN `athlete.id`,
DROP COLUMN `athlete.resource_state`,
DROP COLUMN `map.id`,
DROP COLUMN `map.summary_polyline`,
DROP COLUMN `map.resource_state`,
DROP COLUMN start_date_local;
```
This is what the dataset looks like now:
| Column                        | Dtype     |
|-------------------------------|-----------|
| distance                      | float64   |
| moving_time                   | int64     |
| elapsed_time                  | int64     |
| total_elevation_gain          | float64   |
| type                          | object    |
| start_date                    | object    |
| achievement_count             | int64     |
| average_speed                 | float64   |
| max_speed                     | float64   |
| elev_high                     | float64   |
| elev_low                      | float64   |
| pr_count                      | int64     |

Next, I split the start_date column into two different columns:
1. start_date
2. start_time

We then drop the original start_date column.

```sql
ALTER TABLE activities
ADD COLUMN date DATE,
ADD COLUMN time TIME;

UPDATE activities
SET date = SUBSTRING_INDEX(start_date, 'T', 1),
    time = SUBSTRING_INDEX(SUBSTRING_INDEX(start_date, 'T', -1), 'Z', 1);
    
ALTER TABLE activities
DROP COLUMN start_date;
```

