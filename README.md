# mern_full_stack_mern_reading

## setting up

```bash
mkdir myNewProject
cd myNewProject
touch server.js .gitignore .env
npm init -y
mkdir server
npm i express mongoose dotenv nodemon
npx create-react-app client
```

add the following to [server.js](./myNewProject/server.js)

```js
const express = require('express');
const app = express();
require('dotenv').config();
const port = process.env.PORT;
   
app.listen(port, () => console.log(`Listening on port: ${port}`) );
```
 add the following to [.gitignore](./myNewProject/.gitignore)

```.gitignore
/node_modules
.env
```

add the following to [.env](./myNewProject/.env)

```dotenv
PORT=8000
DB=my_db
# mongo atlas connection
ATLAS_USERNAME=YOUR_ATLAS_USERNAME
ATLAS_PASSWORD=YOUR_ATLAS_PASSWORD
```

## hello world

```bash
mkdir myNewProject/server/controllers && touch myNewProject/server/controllers/person.controller.js 
```

add the following to [person.controller.js](./myNewProject/server/controllers/person.controller.js):

```js
module.exports.index = (request, response) => {
    response.json({
       message: "Hello World"
    });
}
```

```bash
mkdir myNewProject/server/routes && touch myNewProject/server/routes/person.routes.js 
```

add the following to [person.routes.js](./myNewProject/server/routes/person.routes.js):
```js
const PersonController = require('../controllers/person.controller');
module.exports = function(app){
    app.get('/api', PersonController.index);
}
```

update [server.js](./myNewProject/server.js)

```js
const express = require('express');
const app = express();
require('dotenv').config();
const port = process.env.PORT;
    
require('./server/routes/person.routes')(app); // This is new
app.listen(port, () => console.log(`Listening on port: ${port}`) );


```

### React

```bash
cd ./myNewProject/client
npm install axios
touch  src/Main.js
```
update [Main.js](./myNewProject/client/src/Main.js)
```js
import React, { useEffect, useState } from 'react'
import axios from 'axios';
export default () => {
    const [ message, setMessage ] = useState("Loading...")
    useEffect(()=>{
        axios.get("http://localhost:8000/api")
            .then(res=>setMessage(res.data.message))       
    }, []);
    return (
        <div>
            <h2>Message from the backend: {message}</h2>
        </div>
    )
}
```

update [App.js](./myNewProject/client/src/App.js)

```js
import React from 'react';
import Main from './Main';
function App() {
  return (
    <div className="App">
      <Main />
    </div>
  );
}
export default App;


```

## Cors

```bash
npm i cors
```

update [server.js](./myNewProject/server.js)

```js
const express = require('express');
const cors = require('cors') // This is new
const app = express();
require('dotenv').config();
const port = process.env.PORT;
    
app.use(cors()) // This is new
require('./server/routes/person.routes')(app);
app.listen(port, () => console.log(`Listening on port: ${port}`) );
```