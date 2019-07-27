# Contact Keeper API

This is a Node/Express/MongoDB REST API for contacts that uses JWT authentication. All contact endpoints are protected and each registered user has their own contacts.

## Getting Started

```
Open the config/default.json file and add your mongoURI and your jwtSecret
```

```bash
npm install
npm run server # Runs on http://llocalhost:5000
```

# API Usage & Endpoints

## Register a User : POST /api/users

> Request: add user and request JSON web token

- Headers

  ```
  Content-type: application/json
  ```

- Body

  ```
  {
   "name": "",
   "email": "",
   "password": ""
  }
  ```

> Response: 200 (application/json)

- Body

  ```
  {
   "token": ""
  }
  ```

## Login with a user : POST /api/auth

> Request: Login with credentials to recieve a JSON web token

- Headers

  ```
  Content-type: application/json
  ```

- Body

  ```
  {
    "email": "",
    "password": ""
  }
  ```

> Response: 200 (application/json)

- Body

  ```
  {
    "token": ""
  }
  ```

## Get contacts : GET /api/contacts

> Request: get all contacts of a specific user

- Headers

  ```
  x-auth-token: yourJWT
  ```

> Response: 200 (application/json)

- Body

  ```
  {
    "contacts": []
  }
  ```

## Add new contact : POST /api/contacts

> Request: add a new contact

- Headers

  ```
  x-auth-token: yourJWT
  content-type: application/json
  ```

- Body

  ```
  {
    "name": "",
    "email": "",
    "phone": "",
    "type": "" (personal or professional)
  }
  ```

> Response: 200 (application/json)

- Body

  ```
  {
    "contact": {}
  }
  ```

## Update contact : PUT /api/contacts/:id

> Request: update existing contact

- Parameters

  ```
  id: 1 (number) - A unique identifier of the contact
  ```

- Headers

  ```
  x-auth-token: yourJWT
  content-type: application/json
  ```

- Body

  ```
  {
    "name": "",
    "email": "",
    "phone": "",
    "type":
  }
  ```

> Response: 200 (application/json)

- Body

  ```
  {
    "contact": {}
  }
  ```

## Delete contact : DELETE /api/contacts/:id

> Request: delete existing contact

- Parameters

  ```
  id: 1 (number) - A uniqe identifier of the contact
  ```

- Headers

  ```
  x-auth-token: yourJWT
  ```

> Response: 200 (application/json)

- Body

  ```
  {
    "msg": "Contact removed"
  }
  ```
