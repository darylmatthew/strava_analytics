# Strava Analytics Project
Personal project that takes real Strava data from my own physical activities for data analysis.

Project Goals:
1. Visualise my own performance
2. Gather insights on training performance
3. Predict my marathon pacing based on my historical data

   
## Data Source:
Data collected from the offical Strava API, using my own account's physical activity data.

Thes are the initial columns and their respective data types:
| #  | Column                        | Dtype     |
|----|-------------------------------|-----------|
| 0  | resource_state                | int64     |
| 1  | name                          | object    |
| 2  | distance                      | float64   |
| 3  | moving_time                   | int64     |
| 4  | elapsed_time                  | int64     |
| 5  | total_elevation_gain          | float64   |
| 6  | type                          | object    |
| 7  | sport_type                    | object    |
| 8  | workout_type                  | float64   |
| 9  | id                            | int64     |
| 10 | start_date                    | object    |
| 11 | start_date_local              | object    |
| 12 | timezone                      | object    |
| 13 | utc_offset                    | float64   |
| 14 | location_city                 | float64   |
| 15 | location_state                | float64   |
| 16 | location_country              | float64   |
| 17 | achievement_count             | int64     |
| 18 | kudos_count                   | int64     |
| 19 | comment_count                 | int64     |
| 20 | athlete_count                 | int64     |
| 21 | photo_count                   | int64     |
| 22 | trainer                       | bool      |
| 23 | commute                       | bool      |
| 24 | manual                        | bool      |
| 25 | private                       | bool      |
| 26 | visibility                    | object    |
| 27 | flagged                       | bool      |
| 28 | gear_id                       | object    |
| 29 | start_latlng                  | object    |
| 30 | end_latlng                    | object    |
| 31 | average_speed                 | float64   |
| 32 | max_speed                     | float64   |
| 33 | has_heartrate                 | bool      |
| 34 | heartrate_opt_out             | bool      |
| 35 | display_hide_heartrate_option | bool      |
| 36 | elev_high                     | float64   |
| 37 | elev_low                      | float64   |
| 38 | upload_id                     | int64     |
| 39 | upload_id_str                 | int64     |
| 40 | external_id                   | object    |
| 41 | from_accepted_tag             | bool      |
| 42 | pr_count                      | int64     |
| 43 | total_photo_count             | int64     |
| 44 | has_kudoed                    | bool      |
| 45 | athlete.id                    | int64     |
| 46 | athlete.resource_state        | int64     |
| 47 | map.id                        | object    |
| 48 | map.summary_polyline          | object    |
| 49 | map.resource_state            | int64     |
