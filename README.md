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


## redirect URL

https://oauth.your-domain.com/_oauth


## Host file entries for local testing

Add these rows to /etc/hosts

    127.0.0.1 traefik.your-domain.com
    127.0.0.1 oauth.your-domain.com
    127.0.0.1 app.your-domain.com
    127.0.0.1 admin.your-domain.com

