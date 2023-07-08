# connecting backend and frontend

#### Technologies will be used:
* frontend : React.js
* backend : Node.js, express.js

### There are two ways in which you can connect you frontend with backend:
* method 1: Running frontend and backend servers seperately on different ports and even can be on different ip's, and then connecting both the servers using API calls from frontend.
* method 2: Running frontend and backend servers on same server, or we can say serving static files of frontend from backend server.

## method 1
* In this method you will be creating 2 folder's seperately, one for frontend and one for backend
* In folder ```frontend``` you will be creating React app using ```npx create-react-app .```.
* In folder ```backend``` you will be creating a express server using ```npm init```.
```
├── your full stack app
    ├── frontend
    |   ├── node_modules
    |   ├── public
    |   ├── src
    |   ├── package.json
    |   └── package-lock.json
    |
    └── backend
        ├──index.js
        ├──package.json
        └──package-lock.json
```
* In this method you will be running both servers on different ternimals, and you will make api call from frontend to backend server using ```fetch``` api or ```axios```.
    * running frontend server with ```npm start``` in frontend folder
    ```shell
    cd frontend
    npm start
    ```
    * running backend server with ```node index.js``` or ```nodemon index.js``` (if using nodemon)
    ```shell
    cd backend
    node index.js
    ```

## method 2
* This method is interesting one, In this method you will be running only one server for backend and as well as for frontend.
* Here you will convert all files in ```frontend``` folder into static files, and then we will server those files from backend server, as simple is that.
* first go in ```frontend``` folder and run ```npm run build``` to create an optimized build for your frontend app or simply you are converting frontend app into static files.
```shell
cd frontend
npm run build
```

* now, make a ```views``` directory in ```backend``` folder and copy all content of ```./frontend/build``` to ```./backend/views```.
* now, your folder structure will look like this,
```
├── your full stack app
    ├── frontend
    |   ├── build
    |   |   ├── static
    |   |   |   ...
    |   |   └── index.html
    |   ├── node_modules
    |   ├── public
    |   ├── src
    |   ├── package.json
    |   └── package-lock.json
    |
    └── backend
        ├── views
        |   ├── static
        |   |   ...
        |   └── index.html
        ├── index.js
        ├── package.json
        └── package-lock.json
```
* now you can server your frontend from backend server as your frontend app is in ```views``` folder in form of static files.
```js
// index.js in ./backend/

const express = require('express');

const app = express();

app.use(express.urlencoded());

// all backend routes
app.get('/api', (req, res)=>{
    res.send('this request is handled by backend routes "/api"');
})

// static middleware
app.use(express.static(__dirname + '/views'));

// serving frontend
app.get('/', (req, res)=>{
    res.sendFile(__dirname + '/views/index.html');
})

app.listen('3000', 'localhost', ()=>{
    console.log('server is running on port 3000...');
})
```
* Note: The static middleware should always be present after all backend routes, if you will not do so then your frontend routes managed by ```react-router-dom``` will collide with your backend routes.
* Note: By default, when you refresh a page or directly access a specific URL in a React Router-based frontend, the server will try to handle the request first. due to which the routes which should be handled by frontend that will be handled by backend, obviously backend will not have that route and it will show 404 error.
* To fix the issue specified in the 2nd note you can replace ```'/'``` with ```'*'```, then if you will try to access the frontend routes directly or your will refresh the page then frontend will handle that request instead of backend.
```js
const express = require('express');

const app = express();

app.use(express.urlencoded());

// all backend routes
app.get('/api', (req, res)=>{
    res.send('this request is handled by backend route "/api"');
})

// static middleware
app.use(express.static(__dirname + '/views'));

// serving frontend
app.get('*', (req, res)=>{
    res.sendFile(__dirname + '/views/index.html');
})

app.listen('3000', 'localhost', ()=>{
    console.log('server is running on port 3000...');
})
```
