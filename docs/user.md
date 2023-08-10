# User API Spec

## Register User

Endpoint : POST /api/users

Request Body :

```json
{
  "username" : "novianto",
  "password" : "p123",
  "name" : "M. Novianto Anggoro"
}
```

Response Body (Success):

```json
{
  "data" : "OK"
}
```

Response Body (Failed):

```json
{
  "errors" : "Username must not blank, ???"
}
```

## Login User

Endpoint : POST /api/auth/login

Request Body :

```json
{
  "username" : "novianto",
  "password" : "p123"
}
```

Response Body (Success):

```json
{
  "data" : {
    "token" : "MisalToken",
    "expiredAt" : 8374982 // milisecond
  }
}
```

Response Body (Failed, 401):

```json
{
  "errors" : "Username or password wrong !!!"
}
```

## Get User

Endpoint : GET /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success):

```json
{
  "data" : {
    "username" : "novianto",
    "name" : "M. Novianto Anggoro"
  }
}
```

Response Body (Failed, 401):

```json
{
  "errors" : "Unauthorized !!!"
}
```

## Update User

Endpoint : PATCH /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
  "name" : "M. Novianto", // put if only want to update name
  "password" : "new password" // put if only want to update password
}
```

Response Body (Success):

```json
{
  "data" : {
    "username" : "novianto",
    "name" : "M. Novianto Anggoro"
  }
}
```

Response Body (Failed, 401):

```json
{
  "errors" : "Unauthorized !!!"
}
```

## Logout User

Endpoint : DELETE /api/auth/logout

Request Header :

- X-API-TOKEN : Token (Mandatory)
  Response Body (Success):

```json
{
  "data" : "OK"
}
```