# springboot-oauth2-authenticator-server

Simple example of SpringBoot project for OAuth2 Authentication server using Spring Security and Cloud OAuth2


Retrieve token:

```bash
curl --location --request POST 'http://localhost:8088/oauth/token' \
--header 'Authorization: Basic YXBwOnB3ZA==' \
--form 'scope="mobile"' \
--form 'grant_type="password"' \
--form 'username="rodolfo"' \
--form 'password="rodolfopwd"'
```

Response:

```json
{
    "access_token": "0e485f81-1c92-4292-a691-b5cb652aec10",
    "token_type": "bearer",
    "expires_in": 42458,
    "scope": "mobile"
}
```

---

Retrieve user using a token:

```bash
curl --location --request GET 'http://localhost:8088/user' \
--header 'Authorization: Bearer 0e485f81-1c92-4292-a691-b5cb652aec10'
```

Response:

```json
{
    "authorities": [
        {
            "authority": "ROLE_USER"
        }
    ],
    "details": {
        "remoteAddress": "0:0:0:0:0:0:0:1",
        "sessionId": null,
        "tokenValue": "0e485f81-1c92-4292-a691-b5cb652aec10",
        "tokenType": "Bearer",
        "decodedDetails": null
    },
    "authenticated": true,
    "userAuthentication": {
        "authorities": [
            {
                "authority": "ROLE_USER"
            }
        ],
        "details": {
            "grant_type": "password",
            "scope": "mobile",
            "username": "rodolfo"
        },
        "authenticated": true,
        "principal": {
            "password": null,
            "username": "rodolfo",
            "authorities": [
                {
                    "authority": "ROLE_USER"
                }
            ],
            "accountNonExpired": true,
            "accountNonLocked": true,
            "credentialsNonExpired": true,
            "enabled": true
        },
        "credentials": null,
        "name": "rodolfo"
    },
    "oauth2Request": {
        "clientId": "app",
        "scope": [
            "mobile"
        ],
        "requestParameters": {
            "grant_type": "password",
            "scope": "mobile",
            "username": "rodolfo"
        },
        "resourceIds": [],
        "authorities": [],
        "approved": true,
        "refresh": false,
        "redirectUri": null,
        "responseTypes": [],
        "extensions": {},
        "grantType": "password",
        "refreshTokenRequest": null
    },
    "principal": {
        "password": null,
        "username": "rodolfo",
        "authorities": [
            {
                "authority": "ROLE_USER"
            }
        ],
        "accountNonExpired": true,
        "accountNonLocked": true,
        "credentialsNonExpired": true,
        "enabled": true
    },
    "credentials": "",
    "clientOnly": false,
    "name": "rodolfo"
}
```
