1. Let's start with creating a signup button. Create a component called `SignupButton.js` and set it up.

2. Let's create a styled component for the button.

    ```javascript
    export const AuthButtonStyled = styled.button`
        font-size: 1em;
        padding: 0.25em 1em;
        margin-left: 0.5em;
        border-radius: 3px;
        background-color: ${(props) => props.theme.pink};
        color: ${(props) => props.theme.backgroundColor};
    `;
    ```

3. Import the styled component in `SignupButton` and render it.

    ```javascript
    import React from "react";
    import { AuthButtonStyled } from "./styles";

    const SignupButton = () => {
    return (
        <AuthButtonStyled>Sign up</AuthButtonStyled>
    );
    };

    export default SignupButton;
    ```

4. Render the button in `NavBar` right above the `ThemeButton`.

    ```javascript
    <SignupButton />
    <ThemeButton className="nav-item" onClick={toggleTheme}>
        {currentTheme === "light" ? "Dark" : "Light"} Mode
    </ThemeButton>
    ```

