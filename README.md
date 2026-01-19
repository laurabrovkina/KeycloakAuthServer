### Keycloak Docker
* We have created a docker-compose file with standard setting to run admin dashboard using Keycloack
* After running docker-compose up:
    * Go to the [Keycloak Admin Console](http://localhost:8080/admin)
    * Log in with the username and password you created earlier

### Settings
* Manage realms first
* Create a client with PKCE
    * Client authentication is off
    * Authentication flow set to Standard
    * PKCE Method is S256
    * Valid redirect URIs is [postman-oauth](http://oauth.pstmn.io/v1/callback)
* Create a user and set credentials for them

#### Postman call
Use Postman for testing:

![OAuth2.0](./Img/OAuth.jpg)
Click `Get New Access Token` and it will open a browser page where you use test user from before to authorise. 
* Login: test@test.com
* Password: 123

There is a link to obtain more default enpdoints: [keycloack_urls](http://localhost:8080/realms/demo/.well-known/openid-configuration).
That's how we could get a user info:
```
postman request 'http://localhost:8080/realms/demo/protocol/openid-connect/userinfo' \
  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJyY0h5Vi1PTHdvZDB4bjFnUE1pRU93eFNHXzFGeWpVSDEtYW9fUm4waklzIn0.eyJleHAiOjE3Njg3NzcwNDMsImlhdCI6MTc2ODc3Njc0MywiYXV0aF90aW1lIjoxNzY4Nzc1NDYyLCJqdGkiOiJvbnJ0cnQ6ZTQ4ZjM2NDctZWUwNC0zNmRmLTZmODctNDRhNjNjMWI0MzUyIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo4MDgwL3JlYWxtcy9kZW1vIiwiYXVkIjoiYWNjb3VudCIsInN1YiI6IjQ1YWIzNmE0LTViNTYtNDk0Yy1hNmVkLTZkOWM4OTlmMGY1ZiIsInR5cCI6IkJlYXJlciIsImF6cCI6InB1YmxpYyIsInNpZCI6IkN5RVR4OUc0Mjd4SVdpX3o3OGFrQ2F3UiIsImFjciI6IjAiLCJhbGxvd2VkLW9yaWdpbnMiOlsiaHR0cDovL29hdXRoLnBzdG1uLmlvIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJvZmZsaW5lX2FjY2VzcyIsInVtYV9hdXRob3JpemF0aW9uIiwiZGVmYXVsdC1yb2xlcy1kZW1vIl19LCJyZXNvdXJjZV9hY2Nlc3MiOnsiYWNjb3VudCI6eyJyb2xlcyI6WyJtYW5hZ2UtYWNjb3VudCIsIm1hbmFnZS1hY2NvdW50LWxpbmtzIiwidmlldy1wcm9maWxlIl19fSwic2NvcGUiOiJvcGVuaWQgcHJvZmlsZSBlbWFpbCIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJuYW1lIjoiVGVzdCBUZXN0IiwicHJlZmVycmVkX3VzZXJuYW1lIjoidGVzdEB0ZXN0LmNvbSIsImdpdmVuX25hbWUiOiJUZXN0IiwiZmFtaWx5X25hbWUiOiJUZXN0IiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIn0.F4ycBH6rlZ3xTALwBJ27fvSgRpqeLE590MU1sGRhmoFPgdIhZDojDEUH2IccS84tZJA47Qsai5P0Y_0MhQ2KestfWTn6s5GnaEAK0NQ1K9dmNyJTwv0R_LOfia_JJDmCQfVfUhWusHdcL9-PjqHbFpyo8I_u3aGBEfEQAEd4XpC7UrrxinWjr18BRX-AtJJF14GLl84Qx4u5Ff0r6iOuST-8B6tSf0Gtw5RxOlOshA4iXBGt1UA-nXu0BeuBzyaSfrd8ASjbTPvSjF5vwdGiFnyclHZG8F6h7B9bmwixa7dStlRz5A8APxnnRj5b0nt_bbL8RM7iiGmn6CWUcrTpTQ' \
  --auth-oauth2-addTokenTo 'header'
  ```
  This call to be successful use a `Scope:openid`. To refresh token, you might click `Refresh`:
  ![refresh](./Img/Expired_token.jpg)

  There is a postman collection with all these examples in a folder `Postman Collection`.

Info is about jwt:

![jwt.io](./Img/jwt.io.jpg)
