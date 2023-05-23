# mern_full_stack_mern_reading

## setting up

```bash
mkdir myNewProject
cd myNewProject
touch server.js .gitignore .env
mkdir server
cd server
npm i express mongoose dotenv nodemon
cd ..
npx create-react-app client
```

add the following to [server.js](server.js)

```js
const express = require('express');
const app = express();
require('dotenv').config();
const port = process.env.PORT;
   
app.listen(port, () => console.log(`Listening on port: ${port}`) );
```
 add the following to [.gitignore](.gitignore)

```.gitignore
/node_modules
.env
```

add the following to [.env](.env)

```dotenv
PORT=8000
DB=my_db
# mongo atlas connection
ATLAS_USERNAME=YOUR_ATLAS_USERNAME
ATLAS_PASSWORD=YOUR_ATLAS_PASSWORD
```