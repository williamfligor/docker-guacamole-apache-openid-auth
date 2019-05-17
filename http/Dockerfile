FROM httpd:2.4

# RUN apt-get install -y libcurl3 ca-certificates \

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        ca-certificates \
        libpcre3 \
        libjansson4 \
        libhiredis0.13 \
        apache2-api-20120211 \
        curl \
        && rm -rf /var/lib/apt/lists/*

RUN  curl -sLS "https://github.com/zmartzone/mod_auth_openidc/releases/download/v2.3.11/libcjose0_0.6.1.4-1.stretch+1_amd64.deb" -o libcjose.deb \
    && dpkg -i libcjose.deb \
    && rm libcjose.deb

RUN curl -sLS "https://github.com/zmartzone/mod_auth_openidc/releases/download/v2.3.11/libapache2-mod-auth-openidc_2.3.11-1.stretch+1_amd64.deb" -o mod_auth_openidc.deb \
    && dpkg -i mod_auth_openidc.deb \
    && rm mod_auth_openidc.deb \
    && ln -s /usr/lib/apache2/modules/mod_auth_openidc.so /usr/local/apache2/modules/mod_auth_openidc.so

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
