1. In `SignupButton`, import `useState` and create a state called `isOpen` that will control our modal.

   ```javascript
   const [isOpen, setIsOpen] = useState(false);
   ```

2. Create methods that are responsible for opening and closing the modal.

   ```javascript
   const closeModal = () => setIsOpen(false);
   const openModal = () => setIsOpen(true);
   ```

3. Create a signup modal component, `SignupModal.js` and set it up. This component receives `isOpen` and `closeModal` as a `prop`.

   ```javascript
   const SignupModal = ({ isOpen, closeModal }) => {
   ```

4. In `SignupButton`, render `SignupModal` and pass it `isOpen` and `closeModal` as `props`.

   ```javascript
   <>
     <AuthButtonStyled>Sign up</AuthButtonStyled>
     <SignupModal isOpen={isOpen} closeModal={closeModal} />
   </>
   ```

5. Give `AuthButtonStyled` an `onClick` event, and pass it `openModal` method.

   ```javascript
   <AuthButtonStyled onClick={openModal}>Sign up</AuthButtonStyled>
   ```
