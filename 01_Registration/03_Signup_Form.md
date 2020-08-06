1. Import `Modal` from `react-modal` and render it and add a `form` tag inside it with all the fields we need. 

    ```javascript
    <Modal
      isOpen={isOpen}
      onRequestClose={closeModal}
      style={modalStyle}
      contentLabel="Example Modal"
    >
      <h3>Signup</h3>
      <form>
      </form>
    </Modal>
    ```

2. Create a state called `user` and give it an initial value of an object that has 5 properties: `username`, `firstName`, `lastName`, `email` and `password`.

    ```javascript
    const [user, setUser] = useState({
        firstName: "",
        lastName: "",
        username: "",
        password: "",
        email: "",
    });
    ```

3. Add a `handleChange` method.

    ```javascript
    const handleChange = (event) => setUser({ ...user, [event.target.name]: event.target.value });
    ```

4. In your `form` tag, add 5 `input` fields: `username`, `firstName`, `lastName`, `email` and `password`. Give every `input` tag a `name`, `value` and pass it `handleChange` to `onChange`.

    ```javascript
    <form>
        <div className="form-group">
            <label>Username</label>
            <input
            name="username"
            value={user.username}
            type="text"
            className="form-control"
            onChange={handleChange}
            />
        </div>
        <div className="form-group row">
            <div className="col-6">
            <label>First Name</label>
            <input
                name="firstName"
                value={user.firstName}
                type="text"
                className="form-control"
                onChange={handleChange}
            />
            </div>
            <div className="col-6">
            <label>Last Name</label>
            <input
                name="lastName"
                value={user.lastName}
                type="text"
                className="form-control"
                onChange={handleChange}
            />
            </div>
        </div>
        <div className="form-group">
            <label>Email</label>
            <input
            name="email"
            value={user.email}
            type="text"
            className="form-control"
            onChange={handleChange}
            />
        </div>
        <div className="form-group">
            <label>Password</label>
            <input
            name="password"
            value={user.password}
            type="text"
            className="form-control"
            onChange={handleChange}
            />
        </div>
    </form>
    ```

5. Don't forget to add a button **inside** your `form` tags. We will use `CreateButtonStyled` which we imported from `./styles`.

    ```javascript
    <CreateButtonStyled className="btn float-right" type="submit">
      Sign up
    </CreateButtonStyled>
    ```

