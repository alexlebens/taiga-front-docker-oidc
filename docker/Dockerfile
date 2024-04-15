FROM taigaio/taiga-front:6.7.7

LABEL version="6.7.7"
LABEL description="Taiga-Front image that includes the OpenID Plugin."

ARG TAIGA_FRONT_ROOT=/usr/share/nginx/html

ADD config/ /tmp/

RUN set -eux; \ 
    apk update; \
    apk add --no-cache \
        git \
        jq; \        
    git clone https://github.com/taigaio/taiga-contrib-oidc-auth.git; \
    cd taiga-contrib-oidc-auth/front; \
    npm install; \
    npm install gulp; \
    ./node_modules/.bin/gulp build; \
    mkdir -p ${TAIGA_FRONT_ROOT}/plugins/; \
    cp -r dist/ ${TAIGA_FRONT_ROOT}/plugins/oidc-auth/; \
    jq -s 'add' /tmp/conf.json ${TAIGA_FRONT_ROOT}/conf.json >> ${TAIGA_FRONT_ROOT}/conf.json; \
    apk del --no-cache \
        git \
        jq; \
