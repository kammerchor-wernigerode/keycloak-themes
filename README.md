# keycloak-themes

Keycloak is an authorization provider that implements the OAuth2 and OpenID Connect protocols. It manages software
clients, users, their roles and claims for the project.

This project contains a custom theme that captures the look and feel of the organization's corporate design.


## Users

Keycloak is preconfigured with a variety of users that are more or less useful. The username-password-combination
`admin:admin` might be the only one you ever need for development and manual testing.

| Username             | Password             | Description            | Realm  | URL                                         |
|----------------------|----------------------|------------------------|--------|---------------------------------------------|
| <mark>`admin`</mark> | <mark>`admin`</mark> | Realm superuser        | local  | http://localhost:8180/admin/local/console/  |
| `admin`[^1]          | `admin`[^1]          | Keycloak administrator | master | http://localhost:8180/admin/master/console/ |

[^1]: Corresponds to the values of `KEYCLOAK_ADMIN` and `KEYCLOAK_ADMIN_PASSWORD`, set for Composes' _keycloak_ service.


## Configuration Export

This section explains how to export updated configurations so that they can be managed by Git. The development
configuration for Keycloak is part of this project to distribute changes through Git.

First, make sure your development stack is up and running. Perform your necessary changes in the Keycloak web UI. Next,
perform the following command. This will start a new Keycloak instance inside the running container and exports the
_local_ realm and its users.

```shell
 $ docker compose -f docker-compose.yml -f docker-compose.yml exec keycloak \
       /opt/keycloak/bin/kc.sh export --dir /opt/keycloak/data/import --realm local --users realm_file
```
