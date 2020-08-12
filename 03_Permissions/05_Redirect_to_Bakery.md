When a vendor signs in, we need to redirect them directly to their bakery detail page.

1. (SKIP THIS STEP IF YOU'RE USING A SIGNIN MODAL) In the `Signin` component, add a condition. If the user is a `vendor` and has a bakery slug redirect them to the detail page, else redirect them to the home page.

   ```javascript
   if (authStore.user) {
     return (
       <Redirect
         to={
           authStore.user.bakerySlug
             ? `/bakeries/${authStore.user.bakerySlug}`
             : "/"
         }
       />
     );
   }
   ```

2. For the `Signup`, the user doesn't have a bakery when they first sign up, so we redirect them to the home page directly.

3. Now in the `HomePage`, we will add a condition. If the user has a bakery slug redirect them to the detail page.

   ```javascript
   if (authStore.user.bakerySlug)
     return <Redirect to={`/bakeries/${authStore.user.bakerySlug}`} />;
   ```

   Now if the user doesn't have a bakery, we want to open the modal automatically but that will mess up the code for us. So in `NavBar` we will add a modal state, and a button. When this button is clicked, the `BakeryModal` is opened.

4. Start with adding an `isOpen` state and methods to open and close the modal in `NavBar`.

   ```javascript
   const [isOpen, setIsOpen] = useState(false);

   const closeModal = () => setIsOpen(false);
   const openModal = () => setIsOpen(true);
   ```

5. Add a button right above the `ThemeButton` in `NavBar`. We'll use the same styling we used for the greeting, and pass it the `openModal` method.

   ```javascript
   <UsernameStyled onClick={openModal}>Create Bakery</UsernameStyled>
   ```

6. Add a condition so that this button only appears when the user is logged in and does not have a `bakerySlug`.

   ```javascript
   {
     authStore.user && !authStore.user.bakerySlug && (
       <UsernameStyled onClick={openModal}>Create Bakery</UsernameStyled>
     );
   }
   <BakeryModal isOpen={isOpen} closeModal={closeModal} />;
   ```

7. Test it out. Try creating a bakery.
