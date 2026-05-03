# Spotify-Sql-data-analysis

## Overview
This project analyzes a dataset of 1,000+ Spotify songs using SQL to identify trends in song popularity and artist performance.

## Tools Used
SQL

## Key Analysis
- Ranked songs based on popularity to identify top-performing tracks
- Analyzed artists with the most high-popularity songs (popularity > 90)
- Identified the top-performing artist and their most popular songs
- Explored both the highest and lowest popularity songs in the dataset

## Sample Queries

### Top 10 Most Popular Songs
```sql
SELECT song_name, artist_name, popularity
FROM spotifytop1000
ORDER BY popularity DESC
LIMIT 10;
```

### Artists with most high-popularity songs
```sql
SELECT artist_name, COUNT(*) AS total_songs
FROM spotifytop1000
WHERE popularity > 90
GROUP BY artist_name
ORDER BY total_songs DESC
Artists w/ song that has a popularity score >= 90
```

### Top Artist + High-popularity songs
```sql
SELECT artist_name, song_name, popularity
FROM spotifytop1000
WHERE popularity > 90
AND artist_name = (
    SELECT artist_name
    FROM spotifytop1000
    WHERE popularity > 90
    GROUP BY artist_name
    ORDER BY COUNT(*) DESC
);
```

### Lowest Popularity songs
```sql
SELECT song_name, artist_name, popularity
FROM spotifytop1000
ORDER BY popularity ASC
LIMIT 5;
```

