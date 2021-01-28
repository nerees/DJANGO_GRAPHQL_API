# DJANGO_GRAPHQL_API
Initial boilerplate Django and Graphql api for create login users

CHANGE ANG HIDE YOUR SECRET KEY - THIS ONE IS JUST AS EXAMPLE

Just make migrations run local server create user and can try login for example with postman or any api client
```
Local running server: http://127.0.0.1:8000/graphql
```


REGISTER USER:
```
mutation {
  register(
    email: "new_user@email.com",
    username: "new_user",
    password1: "supersecretpassword",
    password2: "supersecretpassword",
  ) {
    success,
    errors,
    token,
    refreshToken
  }
}
```
Save user id and token from link generated for email in console

CHECK IF USER EXISTS:
```
query {
  users (last: 1){
    edges {
      node {
        id,
        username,
        email,
        isActive,
        archived,
        verified,
        secondaryEmail
      }
    }
  }
}
```
VERIFY USER:
```
mutation {
  verifyAccount(token: "YOUR TOKEN HERE") {
    success,
    errors
  }
}
```
CHECK USER INFO
```
query {
  user (id: "<USER ID>"){
    username,
    verified
  }
}
```
LOGIN GraphQL:
```
mutation {
  tokenAuth(username: "new_user", password: "supersecretpassword") {
    success,
    errors,
    unarchiving,
    token,
    refreshToken,
    unarchiving,
    user {
      id,
      username,
    }
  }
}
```
LOGIN POSTMAN: LINK: http://127.0.0.1:8000/graphql
```
mutation {
  tokenAuth(username: "test", password: "supersecretpassword") {
    success,
    errors,
    unarchiving,
    token,
    refreshToken,
    unarchiving,
    user {
      id,
      username,
    }
  }
}
```
