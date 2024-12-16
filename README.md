# Create a Database and a Movies Table

## Step 1: Create the Database and Table

### 1. Create the database:
```sql
CREATE DATABASE MoviesDB;
```

### 2. Switch to the database:
```sql
USE MoviesDB;
```

### 3. Create the Movies table:
```sql
CREATE TABLE Movies (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Title VARCHAR(255),
    Runtime INT,
    Genre VARCHAR(50),
    IMDB_Score DECIMAL(3,1),
    Rating VARCHAR(10)
);
```

### 4. Insert the provided movies:
```sql
INSERT INTO Movies (Title, Runtime, Genre, IMDB_Score, Rating) VALUES
('Howard the Duck', 110, 'Sci-Fi', 4.6, 'PG'),
('Lavalantula', 83, 'Horror', 4.7, 'TV-14'),
('Starship Troopers', 129, 'Sci-Fi', 7.2, 'PG-13'),
('Waltz With Bashir', 90, 'Documentary', 8.0, 'R'),
('Spaceballs', 96, 'Comedy', 7.1, 'PG'),
('Monsters Inc.', 92, 'Animation', 8.1, 'G');
```

### 5. Add two new movies:
```sql
INSERT INTO Movies (Title, Runtime, Genre, IMDB_Score, Rating) VALUES
('i-Robot', 148, 'Sci-Fi', 8.8, 'PG-13'),
('The Conjuring', 112, 'Horror', 7.5, 'R');
```

---

## Step 2: SQL Queries to Answer Questions

### 1. Find all movies in the Sci-Fi genre:
```sql
SELECT * FROM Movies WHERE Genre = 'Sci-Fi';
```

### 2. Find all films that scored at least a 6.5 on IMDB:
```sql
SELECT * FROM Movies WHERE IMDB_Score >= 6.5;
```

### 3. Find movies rated G or PG under 100 minutes long:
```sql
SELECT * FROM Movies 
WHERE (Rating = 'G' OR Rating = 'PG') AND Runtime < 100;
```

### 4. Show average runtimes of movies scoring below 7.5, grouped by genre:
```sql
SELECT Genre, AVG(Runtime) AS Average_Runtime 
FROM Movies 
WHERE IMDB_Score < 7.5 
GROUP BY Genre;
```

### 5. Update "Starship Troopers" rating to R:
```sql
UPDATE Movies 
SET Rating = 'R' 
WHERE Title = 'Starship Troopers';
```

### 6. Show ID number and rating for Horror and Documentary movies:
```sql
SELECT ID, Rating FROM Movies 
WHERE Genre = 'Horror' OR Genre = 'Documentary';
```

### 7. Find average, maximum, and minimum IMDB scores for each rating:
```sql
SELECT Rating, 
       AVG(IMDB_Score) AS Average_Score, 
       MAX(IMDB_Score) AS Max_Score, 
       MIN(IMDB_Score) AS Min_Score 
FROM Movies 
GROUP BY Rating;
```

### 8. Show ratings with multiple movies:
```sql
SELECT Rating, COUNT(*) AS Movie_Count 
FROM Movies 
GROUP BY Rating 
HAVING COUNT(*) > 1;
```

### 9. Make the list child-friendly (delete movies with a rating of R):
```sql
DELETE FROM Movies 
WHERE Rating = 'R';
```

---

## Step 3: Cleanup Commands

### 1. Delete the Movies Table:
```sql
DROP TABLE Movies;
```

### 2. Delete the Database:
```sql
DROP DATABASE MoviesDB;
```
