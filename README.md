# Sample Traefik app


Based on this article: https://daquinoaldo.medium.com/traefik-docker-oauth-a-free-reverse-proxy-with-tsl-and-google-oauth2-da9aa0df96cc


## Start the API Gateway

    docker-compose -f docker-compose-gw.yml up -d

## Start the apps

    docker-compose -f docker-compose-apps.yml up -d


## URLs

    # traefik dashboard
    open http://localhost:8080/dashboard/
    open http://traefik.your-domain.com/dashboard/

    # should redirect to https, no login required
    open http://app.your-domain.com

    # should redirect to https, requires login
    open http://admin.your-domain.com

    # logout url
    open https://oauth.your-domain.com/_oauth/logout

## redirect URL

https://oauth.your-domain.com/_oauth


## Host file entries for local testing

Add these rows to /etc/hosts

    127.0.0.1 traefik.your-domain.com
    127.0.0.1 oauth.your-domain.com
    127.0.0.1 app.your-domain.com
    127.0.0.1 admin.your-domain.com

## Roadmap

### enable JWT on all endpoints 

This isn't possible with the current [thomseddon/traefik-forward-auth](https://github.com/thomseddon/traefik-forward-auth), it is probably possible with [oauth2-proxy](https://github.com/oauth2-proxy/oauth2-proxy). Also see [this article](https://joeeey.com/blog/selfhosting-sso-with-traefik-oauth2-proxy-part-2/) and [this repo](https://github.com/jonananas/traefik-oauth2-proxy/blob/main/docker-compose.yml).

