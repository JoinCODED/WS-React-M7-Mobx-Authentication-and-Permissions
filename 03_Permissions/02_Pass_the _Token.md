To make an `axios` request to an endpoint that requires the user to be logged in, we need to pass the token to each of those endpoints' headers.

What's cool about `axios` is that we can set the token when we first log in, and it'll send it along with any request that requires a token.

1. In `authStore`'s `signin` method, after receiving the token in the response, we will save it in our `axios`'s `instance`.

   ```javascript
   try {
     const res = await instance.post("/signin", userData);
     instance.defaults.headers.common.Authorization = `Bearer ${res.data.token}`;
     this.user = decode(res.data.token);
   }
   ```

2. Let's login and create a new bakery, as it requires the user to be logged in.

3. It worked! We created a bakery while authenticated!

4. Let's do the same thing in `signup`, but wait. The code is becoming very repeated.

5. Let's create a function called `setUser` in `AuthStore` that takes a token as an argument, saves it in the headers, decodes it and saves the decoded object in `this.user`.

   ```javascript
   setUser = (token) => {
     instance.defaults.headers.common.Authorization = `Bearer ${token}`;
     this.user = decode(token);
   };
   ```

6. Call this method in `signin` and pass it the token coming from the response.

   ```javascript
   try {
     const res = await instance.post("/signin", userData);
     this.setUser(res.data.token);
   }
   ```

7. Do the same thing in `signup`.

   ```javascript
   try {
     const res = await instance.post("/signup", userData);
     this.setUser(res.data.token);
   }
   ```
