# connecting backend and frontend

#### Technologies will be used:
* frontend : React.js
* backend : Node.js, express.js

### There are two ways in which you can connect you frontend with backend:
* method 1: Running frontend and backend servers seperately on different ports and even can be on different ip's, and then connecting both the servers using API calls from frontend.
* method 2: Running frontend and backend servers on same server, or we can say serving static files of frontend from backend server.

## method 1
* In this method you will be creating 2 folder's seperately, one for frontend and one for backend
* In folder ```frontend``` you will be creating React app using ```npx create-react-app .```
* In folder ```backend``` you will be creating a express server using ```npm init```.
```
// folder structure
- frontend
    - src
    - public
    - package.json
    - package-lock.json
- backend
    - index.js
    - package.json
    - package-lock.json
```
* In this method you will be running both servers on different ternimals, and you will make api call from frontend to backend server using ```fetch``` api or ```axios```.
    * running frontend server with ```npm start``` in frontend folder
    ```
    cd frontend
    npm start
    ```
    * running backend server with ```node index.js``` or ```nodemon index.js``` (if using nodemon)
    ```
    cd backend
    node index.js
    ```
