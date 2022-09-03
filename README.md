# Add oauth2 to a container with a few lines.

OAuth2 Proxy is a reverse proxy and static file server that provides authentication using third-party providers like Google, GitHub, and others for validating accounts by email, domain, or group.

Oauth2 Proxy is useful when you want:

- One or more of your applications to be accessible only by authenticated users, for instance, users using a specific domain, emails whitelisting, and more
- To rely on a third-party provider to handle the authentication process (Google, GitHub, etc.)
- To keep a clear separation between the authentication service and the rest of your applications

```
docker-compose up -d
```

[oauth2proxy - documentation ](https://github.com/oauth2-proxy/oauth2-proxy)
