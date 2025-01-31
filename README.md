# SQL Analysis Repository

This repository contains complex SQL queries, including joins and window functions, to perform analysis on a database with the following tables:
- Players
- Players Attributes
- Teams
- Leagues
- National Teams

## Overview

The goal of this repository is to use SQL to uncover interesting facts and insights about various leagues, teams, and players. The analysis is performed using a SQLite database.

## Getting Started

### Prerequisites

- Python 3.x
- SQLite
- Jupyter Notebook
- Required Python libraries: `sqlite3`, `pandas`, `numpy`

### Usage

1. Open the Jupyter Notebook:
    ```sh
    jupyter notebook queries.ipynb
    ```
2. Run the cells in the notebook to execute the SQL queries and view the results.

## Database Tables

The `database.sqlite` contains the following tables:
- `Player`: Information about players.
- `Player_Attributes`: Attributes and performance metrics of players.
- `Team`: Information about teams.
- `League`: Information about leagues.
- `Match`: Information about Match days.
- `Country`: Information about the country the leagues are played.
- `Team_Attributes`: Attributes and performance metrics of teams.
## Example Queries

- Counting the number of players in the database:
    ```sql
    SELECT count(*) FROM Player;
    ```

- Finding the top players in each league:
    ```sql
    SELECT p.name, l.name as league, pa.overall_rating
    FROM Player p
    JOIN Player_Attributes pa ON p.player_api_id = pa.player_api_id
    JOIN Team t ON pa.team_api_id = t.team_api_id
    JOIN League l ON t.league_id = l.league_id
    ORDER BY pa.overall_rating DESC
    LIMIT 10;
    ```

- Analyzing player performance trends over time:
    ```sql
    SELECT p.name, pa.date, pa.overall_rating
    FROM Player p
    JOIN Player_Attributes pa ON p.player_api_id = pa.player_api_id
    ORDER BY pa.date;
    ```

- More complex queries involving joins and window functions can be found in the notebook.

## Results

The results of the SQL queries provide insights such as:
- The top players in each league based on various performance metrics.
- The most successful teams in different leagues.
- Comparative analysis of player attributes across different teams and leagues.
- Trends and patterns in player performance over time.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or new queries.

## License

This project is licensed under the MIT License.