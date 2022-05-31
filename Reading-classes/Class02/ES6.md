# Reading: Class 02

## Express Routing
Create, read, update, and delete (CRUD) are the four basic operations of persistent storage 


```js
GET example app.get('path',handlePathfunction);
```
```js
POST (add) example app.POST('path',handlePathfunction);
```
```js
PUT (update) example app.PUT('path',handlePathfunction);
```
```js
DELETE example app.DELETE('path',handlePathfunction);
```

A route method is derived from one of the HTTP methods, and is attached to an instance of the express class.

## Router Handler 

Its basically a callback function that you want to excute with the specific rout is being called.
```js
app.get("/data", (req, res) => {
    res.json({
        id: 1,
        name: 'hamzeh Fakhreddin',
        email: 'hamzabashar2000@gmail.com'
    });
});
```

For example you can handle a specific Error 

```js
module.exports = (req, res, next) => {
    res.status(404).send({
        code: 404,
        route: req.path,
        message: "page not found!",
    });
};
```

To require the app in your server 

```js
const express = require('express');
const app = express();
// to start the app on a port you already defined
function start(port) {
    app.listen(port, () => {
        console.log(`i'm listening on port${port}`);
    });
}
```

## Middlewares

code that runs before the final route call back.
They are in the middle of the beginning of the route and the 
callback function.

```js 
module.exports = (req, res, next) => {
    req.timeStamp = new Date();
    next();
}

```