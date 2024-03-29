# Learn Restify

- Simple RESTful service using Restify.
- Data served by mlab mongodb.

## Configuration

Edit config.js 
```
module.exports = {
    ENV: process.env.NODE_ENV || 'development',
    PORT: process.env.PORT || 3000,
    URL: process.env.BASE_URL || 'http://localhost:3000',
    MONGODB_URI: process.env.MONGODB_URI || 'mongodb_uri,
    JWT_SECRET: process.env.JWT_SECRET || 'secret1'
}
```

## Run

Development mode uses nodemon for live update.
```
npm run dev
```

Deployment mode
```
npm run start
```

## Usage

1. Add user by "Register user" endpoints.
2. Auth registered user by "Auth user" endpoints. You will get JWT (Json Web Token) from service.
3. Add some customers by "Add customer" endpoings. You need JWT generated by "Auth user" access.
4. Get, Update, Delete customers.

## Endpoints

|Function|URL|Headers|Body|
|-|-|-|-|
|Register user|POST<br/>/register|Content-Type: application/json|{ "email": xxxx, "password": xxxxx }|
|Auth user|POST<br/>/auth|Content-Type: appplication/json|{ "email": xxxx, "password": xxxxx }|
|Get customers|GET<br/>/customers|Authorization: jwt generated-token by 'Auth User'|-|
|Get single customer|GET<br/>/customers/id|Authorization: jwt generated-token by 'Auth User'|-|
|Add customer|POST<br/>/customers|Content-Type: application/json<br/>Authorization: jwt generated-token by 'Auth User'|{ "name": XXXX, "email": XXXXXX, "balance": 999}|
|Update customer|PUT<br/>/customers/id|Content-Type: application/json<br/>Authorization: jwt generated-token by 'Auth User'|{ "name": XXXX, "email": XXXXXX, "balance": 999}|
|Delete customer|DELETE<br/>/customers/id|Authorization: jwt generated-token by 'Auth User'|-|

