1. Let's start with creating a logout button. In `NavBar`, import `FiLogOut` icon from `react-icons`.

   ```javascript
   import { FiLogOut } from "react-icons/fi";
   ```

2. Render it under the `Hello, {username}` so that it will only show if the user is logged in. We'll fix the styling a bit.

   ```javascript
   <>
     <UsernameStyled>Hello, {authStore.user.username}</UsernameStyled>
     <FiLogOut onClick={authStore.signout} size="2em" color="red" />
   </>
   ```

3. In `authStore`, create a `signout` method. But how can you logout the user? By setting `this.user` to `null` and deleting the token from the `instance` headers.

   ```javascript
   signout = () => {
     delete instance.defaults.headers.common.Authorization;
     this.user = null;
   };
   ```
