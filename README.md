# taiga-front-docker-oidc

Taiga-Front image that includes the OpenID Plugin.

[taiga-front](https://github.com/taigaio/taiga-front)

[taiga-contrib-oidc-auth](https://github.com/taigaio/taiga-contrib-oidc-auth)


## Workflows

[![release-image](https://github.com/alexlebens/taiga-front-docker-oidc/actions/workflows/release-image.yml/badge.svg)](https://github.com/alexlebens/taiga-front-docker-oidc/actions/workflows/release-image.yml)


## Enviromental Variable

Docker entrypoint script was modifed to include a env to enable OIDC login.

```
ENABLE_OIDC: "True"
```

File was modified from [config_env_subst.sh](https://github.com/taigaio/taiga-front/blob/main/docker/config_env_subst.sh)
