To keep the user logged in we need to save the token in the local storage.

1. In our `setUser` method we will save our token in the `localStorage` using the `setItem` method.

   ```javascript
   setUser = (token) => {
     localStorage.setItem("myToken", token);
     instance.defaults.headers.common.Authorization = `Bearer ${token}`;
     this.user = decode(token);
   };
   ```

   The next question is when do we want to fetch the token? When the application first starts! But first we need to check if the token actually exists and that it's not expired.

2. Let's create a method called `checkForToken` in `authStore`, where we will fetch the token from the local storage. Let's console log it now.

   ```javascript
   checkForToken = () => {
     const token = localStorage.getItem("myToken");
     console.log("checkForToken -> token", token);
   };
   ```

3. But where will we call this function? When the application first starts! So that means right after creating our store!

   ```javascript
   const authStore = new AuthStore();
   authStore.checkForToken();

   export default authStore;
   ```

4. Now we will check if the token exists, if it does we will make sure it's not expired. If it's not we will pass the token to `this.setUser` else we will call `this.signout`.

```javascript
checkForToken = () => {
  const token = localStorage.getItem("myToken");
  if (token) {
    const currentTime = Date.now();
    const user = decode(token);
    if (user.exp >= currentTime) {
      this.setUser(token);
    } else {
      this.signout();
    }
  }
};
```

5. One more thing, if the token is expired we must delete it from our local storage. In `signout`, remove the token from the local storage.

   ```javascript
   signout = () => {
     delete axios.defaults.headers.common.Authorization;
     localStorage.removeItem("myToken");
     this.user = null;
   };
   ```
