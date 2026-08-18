
2026-05-18

Tags: [[Web Security]] [[Networking]]
# Oauth2
## Essentials
1. **Users shouldn't have redirect control:**  Clients and Authorization Server must not expose URLs that forward the user's browser to arbitrary URIs obtained from a query parameter ("open redirectors") which can enable exfiltration of authorization codes and access tokens.
2. **take measures against CSRF attacks:** Clients have ensured that the Authorization Server supports PKCE (Private Key for Code Exchange) may rely on the CSRF protection provided by PKCE. In OpenID Connect flows, the "nonce" parameter provides CSRF protection. Otherwise, one-time user CSRF tokens carried in the "state" parameter that are securely bound to the user agent must be used for CSRF protection.
3. **if multiple auth servers track the issuer:** When an OAuth Client can interact with more than one Authorization Server, Clients should use the issuer `iss` parameter as a countermeasure, or based on an `iss` value in the authorization response (such as the `iss` Claim in the ID Token in OpenID)
4. **if other auth server segmentation isn't possible use distinct URL's:** When the other countermeasure options for OAuth clients interacting with more than one Authorization Servers are absent, Clients may instead use distinct redirect URIs to identify authorization endpoints and token endpoints.
5. An Authorization Server avoids forwarding or redirecting a request potentially containing user credentials accidentally.

Try to use asymmetric keys where possible since it limits how important the secret key is, unlike with a symmetric method.

## In FastAPI
If we are talking about Username/Password then FastAPI actually provides a predetermined "flow" that is built to handle that endpoint. It as designed so that FastAPI is handling the security and authorization, all the frontend has to do is send that user/password to our endpoint and it will receive a token. 
```Python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")


@app.get("/items/")
async def read_items(token: Annotated[str, Depends(oauth2_scheme)]):
    return {"token": token}
```

The following example uses a bearer token, and it certainly isn't the only option. What this code does is It will go and look in the request for that `Authorization` header, check if the value is `Bearer` plus some token, and will return the token as a `str`. If it doesn't see an `Authorization` header, or the value doesn't have a `Bearer` token, it will respond with a 401 status code error (`UNAUTHORIZED`) directly. You don't even have to check if the token exists to return an error. You can be sure that if your function is executed, it will have a `str` in that token.
```python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")


@app.get("/items/")
async def read_items(token: Annotated[str, Depends(oauth2_scheme)]):
    return {"token": token}
```


# References
- [OWASP](https://cheatsheetseries.owasp.org/cheatsheets/OAuth2_Cheat_Sheet.html)
- [FastAPI](https://fastapi.tiangolo.com/tutorial/security/first-steps/#check-it)
- [[CSRF Attacks*]]
- [[Symmetric Cryptography]]
- 
