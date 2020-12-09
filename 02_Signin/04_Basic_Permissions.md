Now, we can use `user` for our conditions. For example, if the user is logged in we don't have to see the signin and signup buttons.

1.  In `Navbar`, import `authStore` and add a condition. If `authStore.user` exists, render the `username`, else render the two buttons

    ```javascript
    {
      authStore.user ? (
        <p>Hello, {authStore.user.username}</p>
      ) : (
        <>
          <SigninButton />
          <SignupButton />
        </>
      );
    }
    ```

2.  Let's fix the styling a bit. Add a new styled component in the `styles` file.

    ```javascript
    export const UsernameStyled = styled.p`
      padding: 0.25em 1em;
    `;
    ```

    Let's spice it up. A user shouldn't see the add cookies icon if they're not logged in.

3.  Go to `BakeryDetail`, import `authStore` and add a condition to render `AddButton`, only if `authStore.user` exists, else render nothing.

    ```javascript
      <CookieList cookies={cookiesFromCookieStore} />
      { authStore.user ? <AddButton bakery={bakery} /> : null}
    </div>
    ```

4.  There's a cleaner way for a condition if it doesn't have an else.

    ```javascript
      <CookieList cookies={cookiesFromCookieStore} />
      { authStore.user && <AddButton bakery={bakery} />}
    </div>
    ```
