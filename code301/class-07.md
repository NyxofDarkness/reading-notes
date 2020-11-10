# Read: 07 - APIs continued

## What Google Learned From Its Quest to Build the Perfect Team

I remeber this from 201. My basic understanding is that collaborative efforts in offices across the country have balooned recently. The encouragement to work together is growing! That means we require more information about teams, how they function, how they work together, and the how to build a complementary team! 

My biggest take away from this article was that it is important to take time to communicate with your team to build trust and reputation among the members. Making sure to be clear and honest so that everyone has a voice that they feel comfortable and safe using. 

## How I explained REST to my brother

> I loved this definition of what HTTP:  is capable of describing the location of something anywhere in the world from anywhere in the world. It's the foundation of the web. You can think of it like GPS coordinates for knowledge and information

> REST provides a definition of a “resource”, which is what those things point to.

> Web services or API =  machines could use the web just like people do.

> URL is so important. It let's all of these systems tell each other about each other's nouns.

> rails is a huge boost for productivity!

## Documentation for SuperAgent

> SuperAgent is light-weight progressive ajax API crafted for flexibility, readability, and a low learning curve after being frustrated with many of the existing request APIs. It also works with Node.js

```
 request
   .post('/api/pet')
   .send({ name: 'Manny', species: 'cat' })
   .set('X-API-Key', 'foobar')
   .set('Accept', 'application/json')
   .then(res => {
      alert('yay got ' + JSON.stringify(res.body));
   });
   ```
> A request can be initiated by invoking the appropriate method on the request object, then calling .then() (or .end() or await) to send the request. For example a simple GET request

```
 request
   .get('/search')
   .then(res => {
      // res.body, res.headers, res.status
   })
   .catch(err => {
      // err.message, err.response
   });
   ```

   > HTTP method may also be passed as a string:
```
request('GET', '/search').then(success, failure);
```

> Setting header fields is simple, invoke .set() with a field name and value
```
 request
   .get('/search')
   .set('API-Key', 'foobar')
   .set('Accept', 'application/json')
   .then(callback);
   ```

   > The .query() method accepts objects, which when used with the GET method will form a query-string. The following will produce the path /search?query=Manny&range=1..5&order=desc.
   ```
    request
   .get('/search')
   .query({ query: 'Manny' })
   .query({ range: '1..5' })
   .query({ order: 'desc' })
   .then(res => {

   });
   ```

   > You can also use the .query() method for HEAD requests. The following will produce the path /users?email=joe@smith.com
   ```
     request
    .head('/users')
    .query({ email: 'joe@smith.com' })
    .then(res => {

    });
    ```
    
I'm bookmarking the rest! This is a very informative list of supporting tags/operations! 
