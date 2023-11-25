Below are some sample queries using Neo4j's Cypher query language on the Movies dataset. The dataset includes nodes representing movies, actors, directors, and genres, and relationships indicating the cast, director, and genre assignments.

### Sample Cypher Queries:

1. **Find all movies and their genres:**
   ```cypher
   MATCH (movie:Movie)-[:IN_GENRE]->(genre:Genre)
   RETURN movie.title, COLLECT(genre.name) AS genres
   ```

2. **Find actors who acted in a specific movie:**
   ```cypher
   MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie {title: 'The Matrix'})
   RETURN actor.name
   ```

3. **Find directors and their movies:**
   ```cypher
   MATCH (director:Director)-[:DIRECTED]->(movie:Movie)
   RETURN director.name, COLLECT(movie.title) AS movies
   ```

4. **Find actors who acted in more than one movie:**
   ```cypher
   MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)
   WITH actor, COUNT(movie) AS moviesCount
   WHERE moviesCount > 1
   RETURN actor.name, moviesCount
   ```

5. **Find movies released in a specific year:**
   ```cypher
   MATCH (movie:Movie)
   WHERE movie.released = 1999
   RETURN movie.title
   ```

6. **Find actors who acted in movies released after 2000:**
   ```cypher
   MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)
   WHERE movie.released > 2000
   RETURN actor.name
   ```

7. **Find the shortest path between two actors:**
   ```cypher
   MATCH path = shortestPath((actor1:Actor)-[*]-(actor2:Actor))
   WHERE actor1.name = 'Keanu Reeves' AND actor2.name = 'Carrie-Anne Moss'
   RETURN path
   ```

8. **Find co-actors of a specific actor:**
   ```cypher
   MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)<-[:ACTED_IN]-(coActor:Actor)
   WHERE actor.name = 'Tom Hanks'
   RETURN DISTINCT coActor.name
   ```

9. **Find movies with a specific genre:**
   ```cypher
   MATCH (movie:Movie)-[:IN_GENRE]->(genre:Genre {name: 'Action'})
   RETURN movie.title
   ```

10. **Find the top 5 genres with the most movies:**
    ```cypher
    MATCH (movie:Movie)-[:IN_GENRE]->(genre:Genre)
    RETURN genre.name, COUNT(movie) AS movieCount
    ORDER BY movieCount DESC
    LIMIT 5
    ```

11. **Find actors who directed a movie:**
    ```cypher
    MATCH (actor:Actor)-[:DIRECTED]->(movie:Movie)
    RETURN actor.name, movie.title
    ```

12. **Find movies where an actor both acted and directed:**
    ```cypher
    MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)<-[:DIRECTED]-(actor)
    RETURN actor.name, movie.title
    ```

13. **Find actors and the genres of movies they acted in:**
    ```cypher
    MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)-[:IN_GENRE]->(genre:Genre)
    RETURN actor.name, COLLECT(DISTINCT genre.name) AS genres
    ```

14. **Find movies with a specific actor and genre:**
    ```cypher
    MATCH (actor:Actor {name: 'Leonardo DiCaprio'})-[:ACTED_IN]->(movie:Movie)-[:IN_GENRE]->(genre:Genre {name: 'Drama'})
    RETURN movie.title
    ```

15. **Find actors and their total movies count:**
    ```cypher
    MATCH (actor:Actor)-[:ACTED_IN]->(movie:Movie)
    RETURN actor.name, COUNT(movie) AS totalMovies
    ORDER BY totalMovies DESC
    ```
