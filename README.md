# Database_Design_For_Spotify ER - ![image](https://github.com/Sree-lekshmi99/Database_Design_For_Spotify/assets/72271005/f319acb6-7d68-4dce-9d7b-8ae08f42bda9)
# Spotify Music Data Management System

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Database](https://img.shields.io/badge/Database-PostgreSQL-blue.svg)](https://www.postgresql.org/)
[![Status](https://img.shields.io/badge/status-Active-green.svg)](https://github.com/your-repo)

## Overview
This project integrates user data with Spotify playlists to provide personalized music insights, optimizing music recommendations based on user preferences. The system replaces Excel with a robust PostgreSQL database solution for handling large datasets, improving query performance, and ensuring data consistency.

## What it Does:
- Integrates Spotify user data and playlist information.
- Provides personalized music recommendations based on preferences (genre, artist, album).
- Ensures real-time data processing for scalable and high-performance recommendations.
- Optimizes playlist and user data management with a PostgreSQL relational database schema.

## Technologies Used:
- **Programming Language:** Python
- **Database:** PostgreSQL (all queries executed in PostgreSQL)
- **Web Framework:** Streamlit
- **Libraries:** SQL, pandas, psycopg2

## Key Features:
- **Data Normalization:** Ensures data integrity and reduces redundancy within the PostgreSQL database.
- **Optimized SQL Queries:** Advanced techniques to improve database performance with PostgreSQL-specific optimizations, such as indexes and optimized joins.
- **Real-Time Data Management:** Efficiently handles millions of music streams, user feedback, and song preferences with PostgreSQL.
- **Scalable Database Schema:** A relational model designed for PostgreSQL to handle large datasets.

## Advantages:
- **Enhanced User Experience:** Real-time, personalized music recommendations.
- **Efficient Data Management:** PostgreSQL is designed to support high concurrency and scalability.
- **Better Performance:** Optimized queries for faster data retrieval and reduced latency.
- **Seamless Integration:** Easily integrates with front-end applications like Streamlit for real-time user interaction.

## SQL Queries
Here are some sample PostgreSQL queries used in the system:

- **Retrieve all the playlists that a specific user owns:**
```sql
SELECT * FROM Playlist WHERE USERID = ?
```

### Retrieve all the playlists that a specific user owns:
```sql
SELECT * FROM Playlist WHERE USERID = ?
Retrieve the total number of songs in each playlist:
```
```sql

SELECT playlist_id, COUNT(track_id) 
FROM Songs_Association 
GROUP BY playlist_id;
```

#Retrieve the top 5 most popular songs:
```sql
SELECT * FROM Song 
ORDER BY track_popularity DESC 
LIMIT 5;
```

#Retrieve artists who have albums released in the last year:
```sql
SELECT artist_name, album_name, COUNT(track_id) 
FROM Artist 
JOIN Album ON Artist.artist_id = Album.artist_id 
JOIN Song ON Album.album_id = Song.track_album 
WHERE release_date > NOW() - INTERVAL '1 year' 
GROUP BY artist_name, album_name;
```
#Identify Users with Most Songs Added to Playlists:
```sql
SELECT u.USERID, COUNT(s.track_id) AS song_count
FROM User u
JOIN Songs_Association sa ON u.USERID = sa.USERID
JOIN Song s ON sa.track_id = s.track_id
GROUP BY u.USERID
ORDER BY song_count DESC;
```
###How to Use:
##Clone the repository:
```bash
git clone https://github.com/your-repo/spotify-music-data-management.git
```
##Install dependencies:
```bash
pip install -r requirements.txt
```
#Set up the PostgreSQL database and configure the connection settings in the config.py file.
#Run the Streamlit app:
```bash
streamlit run app.py
```


Tags
#Spotify, #PostgreSQL, #Database, #MusicRecommendation, #SQL, #Python, #Streamlit, #DataScience, #MachineLearning
