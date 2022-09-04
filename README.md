# Add oAuth2 to a container with a few lines.

OAuth2 Proxy is a reverse proxy and static file server that provides authentication using third-party providers like Google, GitHub, and others for validating accounts by email, domain, or group.

Oauth2 Proxy is useful when you want:

- One or more of your applications to be accessible only by authenticated users, for instance, users using a specific domain, emails whitelisting, and more
- To rely on a third-party provider to handle the authentication process (Google, GitHub, etc.)
- To keep a clear separation between the authentication service and the rest of your applications

For start:
```
docker-compose up -d
```

```
/ping - returns a 200 OK response, which is intended for use with health checks
/metrics - Metrics endpoint for Prometheus to scrape, serve on the address specified by --metrics-address, disabled by default
/oauth2/sign_in - the login page, which also doubles as a sign out page (it clears cookies)
/oauth2/sign_out - this URL is used to clear the session cookie
/oauth2/start - a URL that will redirect to start the OAuth cycle
/oauth2/callback - the URL used at the end of the OAuth cycle. The oauth app will be configured with this as the callback url.
/oauth2/userinfo - the URL is used to return user's email from the session in JSON format.
/oauth2/auth - only returns a 202 Accepted response or a 401 Unauthorized response;
```

- [oauth2proxy - documentation ](https://github.com/oauth2-proxy/oauth2-proxy)

### Others solutions

- [Video oauth2 flow](https://www.youtube.com/watch?v=V36F6xPaaFU)
- [Passport Implementation](https://www.youtube.com/watch?v=Q0a0594tOrc)
- [keycloak + react](https://blog.logrocket.com/implement-keycloak-authentication-react/)
- [keycloak + nest](https://github.com/chamithrepo/nest-keycloak-oauth)


### Keycloak 

Generate password for admin:

```
docker exec local_keycloak \
    /opt/jboss/keycloak/bin/add-user-keycloak.sh \
    -u admin \
    -p admin \
&& docker restart local_keycloak
```

Request token:
```
curl -X POST 'http://localhost:8080/auth/realms/test/protocol/openid-connect/token' \
 --header 'Content-Type: application/x-www-form-urlencoded' \
 --data-urlencode 'grant_type=password' \
 --data-urlencode 'client_id=my-client' \
 --data-urlencode 'username=santiago.blanco@123.com' \
 --data-urlencode 'password=123'
```

Get Realm config
```
http://localhost:8080/auth/realms/test/.well-known/openid-configuration
```
