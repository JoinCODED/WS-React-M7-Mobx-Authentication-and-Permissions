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
