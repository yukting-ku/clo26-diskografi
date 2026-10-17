# SQL-inlämning — Diskografi

**Namn:** Yuk Ting Ku
**Artist:** Ed Sheeran  
**Datum:** 17-10-2026

---

> Lägg länk till eller bild på ditt ER-diagram här:
> `[ER-diagram](er_diagram.png)`

---(https://github.com/yukting-ku/clo26-diskografi/blob/main/ER_diagram.png)

## 1. Skapa databasen — CREATE TABLE

```sql
--- skriv din SQL-kod här ---

```
CREATE TABLE artists (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

--Add artist Ed Sheeran
INSERT INTO artists (id, name)
VALUES (1, 'Ed Sheeran');

CREATE TABLE albums (
    id INTEGER PRIMARY KEY,
    artist_id INTEGER NOT NULL,
    title TEXT NOT NULL,
    release_year INTEGER NOT NULL,
    FOREIGN KEY (artist_id) REFERENCES artists(id)
);

--add 3 albums 
INSERT INTO albums (id, artist_id,title,release_year)
VALUES 
(1, 1, '+', 2011),
(2, 1, 'x', 2014),
(3, 1, '÷ (Divide)', 2017);

CREATE TABLE songs (
    id INTEGER PRIMARY KEY,
    album_id INTEGER NOT NULL,
    title TEXT NOT NULL,
    duration_seconds INTEGER NOT NULL,
    FOREIGN KEY (album_id) REFERENCES albums(id)
);

--add 9 songs in respective to different albums time 
INSERT INTO songs (id, album_id, title, duration_seconds)
VALUES
    (1, 1, 'The A Team', 258),
    (2, 1, 'Lego House', 185),
    (3, 1, 'Give Me Love', 526),
    (4, 2, 'Sing', 235),
    (5, 2, 'Thinking Out Loud', 281),
    (6, 2, 'Photograph', 258),
    (7, 3, 'Shape of You', 234),
    (8, 3, 'Castle on the Hill', 261),
    (9, 3, 'Perfect', 263);

---

## 2. Seeda med data — INSERT

```sql
--- skriv din SQL-kod här ---

```


---

## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---
--list all the albums order by release_year in ascending order 

SELECT *
FROM albums
ORDER BY release_year;


--- query 2: Lista alla låtar på ett specifikt album ---
-- show the title and duration_seconds from the 3rd albums song 

SELECT title, duration_seconds
FROM songs
WHERE album_id = 3;


--- query 3: Antal låtar per album ---
--Join table albums and songs with their respective id and calculate the total songs from each album and group the result by album id and title

SELECT albums.title, COUNT(songs.id) AS song_count
FROM albums
JOIN songs ON albums.id = songs.album_id
GROUP BY albums.id, albums.title;


--- query 4: Längsta låten ---
-- Find the longest song in the database.
SELECT title, duration_seconds
FROM songs
ORDER BY duration_seconds DESC
LIMIT 1;


--- query 5: Alla låtar sorterade alfabetiskt ---

```
-- List all songs in alphabetical ascending order.
SELECT *
FROM songs
ORDER BY title;
---

## 4. Lägg till en ny rad — INSERT

```sql
--- lägg till ett nytt album eller en ny låt ---

```
--insert a temporary test song for the delete function
INSERT INTO songs (id, album_id, title, duration_seconds)
VALUES (10, 1, 'Temporary Test Song', 60);

---

## 5. Ta bort en rad — DELETE

```sql
--- ta bort en rad ur valfri tabell ---

```

--delete the song that we just created
DELETE FROM songs
WHERE id = 10;
---

## 6. Uppdatera en rad — UPDATE

```sql
--- uppdatera minst en rad i valfri tabell ---

```
-- Update the title of a song.
UPDATE songs
SET title = 'The A Team (Test)'
WHERE id = 1;

--checking if its sucessful 
SELECT *
FROM songs
WHERE id = 1;

-- Restore the original title.
UPDATE songs
SET title = 'The A Team'
WHERE id = 1;


---

## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---
--find out the average length of each song from album and group by the albums id and title
SELECT albums.title,
       AVG(songs.duration_seconds) AS average_duration
FROM albums
JOIN songs ON albums.id = songs.album_id
GROUP BY albums.id, albums.title;

--- query 7: Albumet med flest låtar ---
--find out which album has the most amount of song by using the count function and job and album id with song id , group by album id and title

SELECT albums.title,
       COUNT(songs.id) AS song_count
FROM albums
JOIN songs ON albums.id = songs.album_id
GROUP BY albums.id, albums.title
order by song_count desc
LIMIT 1;

--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---

```
--list the song that is more than 240 seconds by joining the album and song id order by songs duration_seconds in descending order 

SELECT songs.title,
       songs.duration_seconds,
       albums.title AS album_title
FROM songs
JOIN albums ON songs.album_id = albums.id
WHERE songs.duration_seconds > 240
ORDER BY songs.duration_seconds DESC;
