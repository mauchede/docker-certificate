FROM alpine:latest

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

RUN set -e -u -x \
\
    # Install packages
\
    && apk add --no-cache --no-progress --virtual BUILD_DEPS curl \
    && apk add --no-cache --no-progress bash openssl \
\
    # Install dumb-entrypoint
\
    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/dumb-entrypoint/installer" | sh -s -- install \
    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/gosu/installer" | sh -s -- install \
\
    # Install omgwtfssl
\
    && curl --location --output /usr/bin/generate-certs "https://github.com/paulczar/omgwtfssl/raw/master/generate-certs" \
    && chmod +x /usr/bin/generate-certs \
\
    # Clean
\
    && apk del --no-progress BUILD_DEPS

ENTRYPOINT [ "dumb-entrypoint" ]
