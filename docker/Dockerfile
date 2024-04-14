FROM taigaio/taiga-front:6.7.7

LABEL version="6.7.7"
LABEL description="Taiga-Front image that includes the OpenID Plugin."

ARG TAIGA_FRONT_ROOT=/taiga

ADD config/ /tmp/

RUN apk update; \
    apk add --no-cache \
        git; \
    apk add --no-cache \
        jq; \        
    git clone https://github.com/taigaio/taiga-contrib-oidc-auth.git; \
    cd taiga-contrib-oidc-auth/front; \
    npm install; \
    npm install gulp; \
    ./node_modules/.bin/gulp build; \
    mkdir -p ${TAIGA_FRONT_ROOT}/dist/plugins/; \
    cp -r dist/ ${TAIGA_FRONT_ROOT}/dist/plugins/oidc-auth/; \
    jq -s 'add' /tmp/conf.json ${TAIGA_FRONT_ROOT}/dist/conf.json >> ${TAIGA_FRONT_ROOT}/dist/conf.json; \
