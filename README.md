# DJANGO_GRAPHQL_API
Initial boilerplate Django and Graphql api for create login users

Just make migrations run local server create user and can try login for example with postman or any api client

Local running server: http://127.0.0.1:8000/graphql



REGISTER USER:
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

Save user id and token from link generated for email in console

CHECK IF USER EXISTS:
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

VERIFY USER:
mutation {
  verifyAccount(token: "YOUR TOKEN HERE") {
    success,
    errors
  }
}

CHECK USER INFO
query {
  user (id: "<USER ID>"){
    username,
    verified
  }
}

LOGIN:
"data": {
        "tokenAuth": {
            "success": true,
            "errors": null,
            "unarchiving": false,
            "token": "xxxxxxxxx",
            "refreshToken": "xxxxxxxxx",
            "user": {
                "id": "xxxxxxxxxx",
                "username": "xxxxxxx"
            }
        }
    }
}
