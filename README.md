# Data modeling with Postgres

This **Udacity Data Engineering nanodegree** project creates a postgres database `sparkifydb` for a music app, *Sparkify*. The purpose of the database is to model song and log datasets (originaly stored in JSON format) with a star schema optimised for queries on song play analysis.



## Schema design and ETL pipeline

The star schema has 1 *fact* table (songplays), and 4 *dimension* tables (users, songs, artists, time). `DROP`, `CREATE`, `INSERT`, and `SELECT` queries are defined in **sql_queries.py**. **create_tables.py** uses functions `create_database`, `drop_tables`, and `create_tables` to create the database sparkifydb and the required tables.

![](star_schema.png?raw=true)

Extract, transform, load processes in **etl.py** populate the **songs** and **artists** tables with data derived from the JSON song files, `data/song_data`. Processed data derived from the JSON log files, `data/log_data`, is used to populate **time** and **users** tables. A `SELECT` query collects song and artist id from the **songs** and **artists** tables and combines this with log file derived data to populate the **songplays** fact table.


## Example queries for Song play

Simple queries might include number of users with each membership level.

`SELECT COUNT(level) FROM users;`

Day of the week music most frequently listened to.

`SELECT COUNT(weekday) FROM time;`

Or, hour of the day music most often listened to.

`SELECT COUNT(hour) FROM time;`

<br>
