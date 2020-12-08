1. In your `authStore` class, create a method called `signin`. This method takes the `userData` as an argument and sends a request to the `/signin` endpoint and passes `userData` in the `body` of the request. When logging in, we expect the token as a response. Let's console log it for now.

   ```javascript
   signin = async (userData) => {
     try {
       const res = await instance.post("/signin", userData);
       console.log("authStore -> signin -> res.data", res.data);
     } catch (error) {
       console.log("AuthStore -> signin -> error", error);
     }
   };
   ```

2. Back to `SigninModal`. Change the `handleSubmit` method to call `authStore.signin` and pass it `user` as an argument.

   ```javascript
   const handleSubmit = (event) => {
     event.preventDefault();
     authStore.signin(user);
     closeModal();
   };
   ```

3. Try logging in and check your console. Yaaay! We got our token!

But now what can we do with the token? We need to decode it!

4. Install `jwt-decode` which is a library that can decode tokens.

   ```javascript
   $ yarn add jwt-decode
   ```

5. Import `decode` from `jwt-decode` which is a function that takes a token as an argument and returns the decoded object.

   ```javascript
   import decode from "jwt-decode";
   ```

6. Pass the token in `res.data` to `jwt-decode` and let's console log it.

   ```javascript
   try {
     const res = await instance.post("/signin", userData);
     console.log(decode(res.data.token));
   }
   ```

7. But what will we do now with this decoded token? We'll create a new property in our store called `user`. `user`'s initial value is `null`, which basically mean that no user is logged in.

   ```javascript
   class AuthStore {
     user = null;
   ```

8. In `signin`, we will save the decoded token in `this.user`.

```javascript
try {
  const res = await instance.post("/signin", userData);
  this.user = decode(res.data.token);
}
```
