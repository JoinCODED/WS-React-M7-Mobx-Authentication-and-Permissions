Let's cleanup our stores a little bit. As you can see all `axios` requests have the same URL beginning. What's cool about `axios` is that it has a method called `create` which you can give your base URL.

1. In your `stores` folder, create a file called `instance.js`. In this file import `axios`.

    ```javascript
    import axios from "axios";
    ```

2. Call `axios.create` which takes an object as an argument, this object has a property called `baseURL` and its value is the base URL of all your requests. Save the return value in a variable called `instance` and export it.

    ```javascript
    const instance = axios.create({
        baseURL: "http://localhost:8000",
    });

    export default instance;
    ```

3. In `authStore`, import `instance`.

    ```javascript
    import instance from "./instance";
    ```

4. Then replace `axios.post` with `instance.post` and remove the base URL.

    ```javascript
    await instance.post("/signup", userData);
    ```

5. Repeat the same with all your requests in `cookieStore` and `bakeryStore`.