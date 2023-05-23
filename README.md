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