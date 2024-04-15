FROM taigaio/taiga-front:6.7.7

LABEL version="6.7.7"
LABEL description="Taiga-Front image that includes the OpenID Plugin."

ARG TAIGA_FRONT_ROOT=/usr/share/nginx/html

COPY config/config_env_subst.sh /docker-entrypoint.d/30_config_env_subst.sh

RUN set -eux; \

    # Install needed apps
    apk update; \
    apk add --no-cache \
        npm \
        git; \

    # Compile and install oidc auth
    git clone https://github.com/taigaio/taiga-contrib-oidc-auth.git; \
    cd taiga-contrib-oidc-auth/front; \
    npm install; \
    npm install gulp; \
    ./node_modules/.bin/gulp build; \
    mkdir -p ${TAIGA_FRONT_ROOT}/plugins/oidc-auth/; \
    cp --verbose -r dist/ ${TAIGA_FRONT_ROOT}/plugins/oidc-auth/; \

    # Remove installed apps
    apk del --no-cache \
        npm \
        git; \
