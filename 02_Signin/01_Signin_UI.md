1. Let's start with creating a signin button. Create a component called `SigninButton.js`, here's the code for it.

   ```javascript
   import React, { useState } from "react";
   import { AuthButtonStyled } from "../../styles";
   import SigninModal from "../modals/SigninModal";

   const SigninButton = () => {
     const [isOpen, setIsOpen] = useState(false);

     const closeModal = () => setIsOpen(false);
     const openModal = () => setIsOpen(true);

     return (
       <>
         <AuthButtonStyled onClick={openModal}>Sign in</AuthButtonStyled>
         <SigninModal isOpen={isOpen} closeModal={closeModal} />
       </>
     );
   };

   export default SigninButton;
   ```

2. Render the button in `NavBar` right above the `ThemeButton`.

   ```javascript
   <SigninButton />
   <ThemeButton className="nav-item" onClick={toggleTheme}>
       {currentTheme === "light" ? "Dark" : "Light"} Mode
   </ThemeButton>
   ```
