Now that the backend is modified to take a role, we need to fix our `signup` method and add the `role` field.

Since this website is for vendors only, all users signing up are obviously vendors. So we will automatically set `role` to `vendor`.

1. In `SignupModal`, we will add a field in our state `user` called `role` and set it to `vendor`.

2. Try creating a new user from the website, then log in. Console log the token to make sure the role is there. Yes it's there!

3. Let's start with the list of cookies and bakeries. Only the admin should see a list of **all** bakeries and cookies! So let's fix our condition to check that a user is logged in and they're logged in.

   ```javascript
   {
     authStore.user && authStore.user.role === "admin" && (
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

4. Let's also fix `CookieList` and `BakeryList`'s conditions.

   ```javascript
   if (!authStore.user || authStore.user.role !== "admin")
     return <Redirect to="/" />;
   ```
