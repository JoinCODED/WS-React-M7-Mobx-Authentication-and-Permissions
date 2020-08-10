Now, we can use `user` for our conditions. For example, if the user is logged in we don't have to see the signin and signup buttons.

1. In `Navbar`, import `authStore` and add a condition. If `authStore.user` exists, render the `username`, else render the two buttons

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

2. Let's fix the styling a bit. Add a new styled component in the `styles` file.

   ```javascript
   export const UsernameStyled = styled.p`
     padding: 0.25em 1em;
   `;
   ```

Let's spice it up. A user shouldn't see the bakeries or cookies if they're not logged in.

3. Let's start with the `Navbar`, if the user isn't logged in we will hide the two links.

   ```javascript
   {
     authStore.user && (
       <>
         <NavItem className="nav-item" to="/bakeries">
           Bakeries
         </NavItem>
         <NavItem className="nav-item" to="/cookies">
           Cookies
         </NavItem>
       </>
     );
   }
   ```

But is that enough? If you go directly to `localhost:8000/cookies` you'll access the cookies list!

4. So we'll add a condition in `CookieList`. If the user is **not** logged in, redirect them to the home page.

   ```javascript
   if (!authStore.user) return <Redirect to="/" />;
   ```

5. Do the same thing for `BakeryList`.
