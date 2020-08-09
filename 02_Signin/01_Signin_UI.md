1. Let's start with creating a signin button. Create a component called `SigninButton.js` and set it up.

2. Import the styled component `AuthButtonStyled` in `SigninButton` and render it.

   ```javascript
   import React from "react";
   import { AuthButtonStyled } from "./styles";

   const SigninButton = () => {
     return <AuthButtonStyled>Sign in</AuthButtonStyled>;
   };

   export default SigninButton;
   ```

3. Render the button in `NavBar` right above the `ThemeButton`.

   ```javascript
   <SigninButton />
   <ThemeButton className="nav-item" onClick={toggleTheme}>
       {currentTheme === "light" ? "Dark" : "Light"} Mode
   </ThemeButton>
   ```

4. Create a new component in `modals` called `SigninModal`.

5. Copy the code from `SignupModal` into `SigninModal`.

6. We only need two `input` fields, `username` and `password`. Remove the extra `input` fields.

7. Remove the extra properties from your `user` state, keep only `username` and `password`.
