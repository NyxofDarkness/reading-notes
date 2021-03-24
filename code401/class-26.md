# Reading

## [Read: JSON Web Tokens](https://jwt.io/introduction/)

> JSON Web Token (JWT) is an open standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON object

> Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties

>  When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

>  scenarios where JSON Web Tokens are useful: 

1. Authorization-Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. 

2. Information Exchange-Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

> JSON Web Tokens consist of three parts separated by dots (.), which are:

1. Header
2. Payload
3. Signature

> The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

``` python
# example
{
  "alg": "HS256",
  "typ": "JWT"
}
```

> payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: 

1. registered, a set of predefined claims which are not mandatory but recommended-Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.

2. public, These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace

3. private claims, custom claims created to share information between parties that agree on using them and are neither registered or public claims.

> example payload:

``` python
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

> To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

> The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

> [ play with JWT and put these concepts into practice, you can use jwt.io](https://jwt.io/#debugger-io)

> In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned

> The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources.

> Process of authorization:

1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.

2. When the authorization is granted, the authorization server returns an access token to the application.

3. The application uses the access token to access a protected resource (like an API).

## [Read: DRF JWT Authentication](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)

> access token is usually short-lived (expires in 5 min or so, can be customized though).

> refresh token lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an authentication session. After it expires, you need a full login with username + password again.

> we are going to use the djangorestframework_simplejwt library

> Start here:

``` python
https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html
```

> in settings.py

``` python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```

> in urls.py

``` python

from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Your URLs...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
```

> Example code using the following route and API view:

> in views.py

``` python
from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework.permissions import IsAuthenticated


class HelloView(APIView):
    permission_classes = (IsAuthenticated,)

    def get(self, request):
        content = {'message': 'Hello, World!'}
        return Response(content)
```

> in urls.py

``` python
from django.urls import path
from myapi.core import views

urlpatterns = [
    path('hello/', views.HelloView.as_view(), name='hello'),
]
```

> First step is to authenticate and obtain the token

> your response body is the two tokens:



``` python
http http://127.0.0.1:8000/hello/ "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQ1MjI0MjAwLCJqdGkiOiJlMGQxZDY2MjE5ODc0ZTY3OWY0NjM0ZWU2NTQ2YTIwMCIsInVzZXJfaWQiOjF9.9eHat3CvRQYnb5EdcgYFzUyMobXzxlAVh_IAgqyvzCE"
```

> https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html

``` python
http http://127.0.0.1:8000/hello/ "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQ1MjI0MjAwLCJqdGkiOiJlMGQxZDY2MjE5ODc0ZTY3OWY0NjM0ZWU2NTQ2YTIwMCIsInVzZXJfaWQiOjF9.9eHat3CvRQYnb5EdcgYFzUyMobXzxlAVh_IAgqyvzCE"
```

> To get a new access token, you should use the refresh token endpoint 

> The refresh token is valid for the next 24 hours. When it finally expires too, the user will need to perform a full authentication again using their username and password to get a new set of access token + refresh token.

> refresh token may look pointless, but in fact it is necessary to make sure the user still have the correct permissions. If your access token have a long expire time, it may take longer to update the information associated with the token

## (Optional) [JWT with DRF](https://www.youtube.com/watch?v=Fhcn2qx-4VQ)

## Bookmark/Skim

-[x] Skim: [Django Migrations Primer](https://realpython.com/django-migrations-a-primer/)
