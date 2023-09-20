###  Optimisation diary
#### This branch is about writing some notes on optimising queries. 
#### I will use example code snippet using PHP or Laravel Framework-specific syntax. But the suggested strategies are well known and applicable to any language or framework.

* Use Eager Loading to prevent N+1 problem 
##### Problem Scenario
```
$posts = Post::all();

foreach ($posts as $post) {
    echo $post->comments;  // This will run a query for each post to get its comments. So developer might have end up with N+1 problem
}
```
#### Solution   
```
$posts = Post::with('comments')->get();

foreach ($posts as $post) {
    echo $post->comments;  // This does not run additional queries since comments are already loaded
}
```
* Database indexing
* Use `select` wisely | Avoid using ` select * ` in RAW SQL 
```
// Instead of
$posts = Post::all();

// Fetch specific columns
$posts = Post::select('id', 'title')->get();
```

* Use Pagination 
* Batch Processing 
* Caching
* Don't write subqueries while writing SQL queries
* Use Limit while fetching data. Use `limit` in RAW SQL and `limit`, '`take` or  'skip` in Laravel to constrain the result
* Normalize database
* Use appropriate datatype


