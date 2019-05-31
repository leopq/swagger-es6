# swagger-es6

Swagger.json to ES6 Client Generator  
![build](https://img.shields.io/appveyor/ci/gruntjs/grunt.svg)  ![platform](https://img.shields.io/node/v/react.svg) ![stars](https://img.shields.io/amo/stars/dustman.svg) ![license](https://img.shields.io/bower/l/bootstrap.svg)  
  
> [![basic-merchandising](https://imgur.com/LNOYczf.png)](https://github.com/leopq)

# Installation

```shell
npm install swagger-es6 --dev
```

# Generate

## Using NodeJS file

```javascript
const swaggerGen = require('swagger-es6')
const jsonData = require('../api-docs.json')
const fs = require('fs')
const path = require('path')

let opt = {
  swagger: jsonData,
  moduleName: 'api',
  className: 'api'
}
const codeResult = swaggerGen(opt)
fs.writeFileSync(path.join(__dirname, '../dist/api.js'), codeResult)
```

# Generated client usage

In JS main file set API domain
```javascript
import { setAPIDomain } from './lib/api-client.js'
const server = "http://localhost:3000/api";
setAPIDomain(server)
```

Import API function into JS component, for example to log in

```javascript
import { user_login as userLogin } from '../lib/api-client.js'

userLogin({
  credentials: {
    username: 'admin',
    password: 'admin'
  }
}).then(function (response) {
  console.log(response.data) // {id: "<token>", ttl: 1209600, created: "2017-01-01T00:00:00.000Z", userId: 1}
})
```

Using authentication header:

```javascript
import { fetch_clients as fetchClients } from '../lib/api-client.js'

fetchClients({
  xAccessToken: 'some_very_secure_token'
}).then(function (response) {
  console.log(response.data) // [{ name: 'Jon', age: 64 }, { name: 'Ada', age: 24 }, { name: 'Alan', age: 38 }]
})
```

All requests use **axios** module with promise, for more information about that follow axios documentation

# Links
 - [swagger-js-codegen](https://github.com/wcandillon/swagger-js-codegen)
 - [axios](https://www.npmjs.com/package/axios)

# License

[MIT](https://opensource.org/licenses/MIT)
````
