Since the `signup` is now returning the token as a response, we need to decode it.

1. In `authStore`'s `signup` method, save the response, and pass the token the `decode` method, and save the return value in `this.user`.

   ```javascript
   try {
     const res = await instance.post("/signup", userData);
     this.user = decode(res.data.token);
   }
   ```

2. Now let's try creating a new user. Yes! It logged us in!
