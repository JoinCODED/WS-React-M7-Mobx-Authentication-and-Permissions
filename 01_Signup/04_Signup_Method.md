1. Create a new store that will be responsible for authentication. Let's call it `authStore.js`.

   ```javascript
   import { observable, makeAutoObservable } from "mobx";
   import axios from "axios";

   class AuthStore {
     constructor() {
       makeAutoObservable(this);
     }
   }

   const authStore = new AuthStore();

   export default authStore;
   ```

2. In your `AuthStore` class, create a method called `signup`. This method takes the `userData` as an argument and sends a request to the `/signup` endpoint and passes `userData` in the `body` of the request.

   ```javascript
   signup = async (userData) => {
     try {
       await axios.post("http://localhost:8000/signup", userData);
     } catch (error) {
       console.log("AuthStore -> signup -> error", error);
     }
   };
   ```

3. Back to `SignupModal`. Create a `handleSubmit` method that calls `authStore.signup` and pass it `user` as an argument.

   ```javascript
   const handleSubmit = (event) => {
     event.preventDefault();
     authStore.signup(user);
     closeModal();
   };
   ```

4. Pass `handleSubmit` to the `form`'s `onSubmit` event.

   ```javascript
   <form onSubmit={handleSubmit}>
   ```

5. Check TablePlus to make sure your new user is created. Voila!
