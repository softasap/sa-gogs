sa-gogs
=======
[![Build Status](https://travis-ci.org/softasap/sa-gogs.svg?branch=master)](https://travis-ci.org/softasap/sa-gogs)


Gogs - A painless self-hosted Git service.


Example of use: check box-example

Simple:

```YAML

gogs_custom_app_ini:
  main:
    APP_NAME: 'Gogs: Go Git Service'
    RUN_USER: 'git'
    RUN_MODE: 'dev'
  repository:
    ROOT: ''
    SCRIPT_TYPE: 'bash'
  server:
    PROTOCOL: 'http'
    DOMAIN: 'localhost'
    ROOT_URL: '%(PROTOCOL)s://%(DOMAIN)s:%(HTTP_PORT)s/'
    HTTP_ADDR: ''
    HTTP_PORT: '3000'
    SSH_PORT: '22'
    OFFLINE_MODE: false
    DISABLE_ROUTER_LOG: false
    CERT_FILE: 'custom/https/cert.pem'
    KEY_FILE: 'custom/https/key.pem'
    STATIC_ROOT_PATH: ''
    ENABLE_GZIP: false
    LANDING_PAGE: 'home'
  database:
    DB_TYPE: mysql
    HOST: 127.0.0.1:3306
    NAME: gogs
    USER: root
    PASSWD: ''
    SSL_MODE: 'disable'
    PATH: 'data/gogs.db'

...

roles:

     - {
         role: "sa-gogs",
         gogs_app_ini: "{{gogs_custom_app_ini}}"         
       }

```

and follow installation wizard for rest of steps

Advanced:

```YAML

gogs_custom_app_ini:
  main:
    APP_NAME: 'Gogs: Go Git Service'
    RUN_USER: 'git'
    RUN_MODE: 'dev'
  repository:
    ROOT: ''
    SCRIPT_TYPE: 'bash'
  server:
    PROTOCOL: 'http'
    DOMAIN: 'localhost'
    ROOT_URL: '%(PROTOCOL)s://%(DOMAIN)s:%(HTTP_PORT)s/'
    HTTP_ADDR: ''
    HTTP_PORT: '3000'
    SSH_PORT: '22'
    OFFLINE_MODE: false
    DISABLE_ROUTER_LOG: false
    CERT_FILE: 'custom/https/cert.pem'
    KEY_FILE: 'custom/https/key.pem'
    STATIC_ROOT_PATH: ''
    ENABLE_GZIP: false
    LANDING_PAGE: 'home'
  database:
    DB_TYPE: mysql
    HOST: 127.0.0.1:3306
    NAME: gogs
    USER: root
    PASSWD: ''
    SSL_MODE: 'disable'
    PATH: 'data/gogs.db'
  security:
    INSTALL_LOCK: false
    SECRET_KEY: '!#@FDEWREWR&*('
    LOGIN_REMEMBER_DAYS: 7
    COOKIE_USERNAME: 'gogs_awesome'
    COOKIE_REMEMBER_NAME: 'gogs_incredible'
    REVERSE_PROXY_AUTHENTICATION_USER: 'X-WEBAUTH-USER'
  service:
    ACTIVE_CODE_LIVE_MINUTES: 180
    RESET_PASSWD_CODE_LIVE_MINUTES: 180
    REGISTER_EMAIL_CONFIRM: false
    DISABLE_REGISTRATION: false
    REQUIRE_SIGNIN_VIEW: false
    ENABLE_CACHE_AVATAR: false
    ENABLE_NOTIFY_MAIL: false
    ENABLE_REVERSE_PROXY_AUTHENTICATION: false
    ENABLE_REVERSE_PROXY_AUTO_REGISTERATION: false
  webhook:
    TASK_INTERVAL: 1
    DELIVER_TIMEOUT: 5
  mailer:
    ENABLED: false
    SEND_BUFFER_LEN: 10
    SUBJECT: '%(APP_NAME)s'
    HOST: ''
    SKIP_VERIFY: ''
    FROM: ''
    USER: ''
    PASSWD: ''
  oauth:
    ENABLED: false
  oauth.github:
    ENABLED: false
    CLIENT_ID: ''
    CLIENT_SECRET: ''
    SCOPES: 'https://api.github.com/user'
    AUTH_URL: 'https://github.com/login/oauth/authorize'
    TOKEN_URL: 'https://github.com/login/oauth/access_token'
  oauth.google:
    ENABLED: false
    CLIENT_ID: ''
    CLIENT_SECRET: ''
    SCOPES: 'https://www.googleapis.com/auth/userinfo.email https://www.googleapis.com/auth/userinfo.profile'
    AUTH_URL: 'https://accounts.google.com/o/oauth2/auth'
    TOKEN_URL: 'https://accounts.google.com/o/oauth2/token'
  oauth.qq:
    ENABLED: false
    CLIENT_ID: ''
    CLIENT_SECRET: ''
    SCOPES: 'get_user_info'
    AUTH_URL: 'https://graph.qq.com/oauth2.0/authorize'
    TOKEN_URL: 'https://graph.qq.com/oauth2.0/token'
  oauth.weibo:
    ENABLED: false
    CLIENT_ID: ''
    CLIENT_SECRET: ''
    SCOPES: 'all'
    AUTH_URL: 'https://api.weibo.com/oauth2/authorize'
    TOKEN_URL: 'https://api.weibo.com/oauth2/access_token'
  cache:
    ADAPTER: 'memory'
    INTERVAL: 60
    HOST: ''
  session:
    PROVIDER: 'memory'
    PROVIDER_CONFIG: 'data/sessions'
    COOKIE_NAME: 'i_like_gogits'
    COOKIE_SECURE: 'false'
    ENABLE_SET_COOKIE: true
    GC_INTERVAL_TIME: 86400
    SESSION_LIFE_TIME: 86400
  picture:
    SERVICE: 'server'
    AVATAR_UPLOAD_PATH: 'data/avatars'
    GRAVATAR_SOURCE: 'gravatar'
    DISABLE_GRAVATAR: false
  attachment:
    ENABLE: true
    PATH: 'data/attachments'
    ALLOWED_TYPES: 'image/jpeg|image/png'
    MAX_SIZE: 32
    MAX_FILES: 10
  time:
    FORMAT: ''
  log:
    ROOT_PATH: ''
    MODE: 'console'
    BUFFER_LEN: 10000
    LEVEL: 'Trace'
  log.console:
    LEVEL: ''
  log.file:
    LEVEL: ''
    LOG_ROTATE: true
    MAX_LINES: 1000000
    MAX_SIZE_SHIFT: 28
    DAILY_ROTATE: true
    MAX_DAYS: 7
  log.conn:
    LEVEL: ''
    RECONNECT_ON_MSG: false
    RECONNECT: false
    PROTOCOL: 'tcp'
    ADDR: ''
  log.smtp:
    LEVEL: ''
    SUBJECT: 'Diagnostic message from serve'
    HOST: ''
    USER: ''
    PASSWD: ''
    RECEIVERS: ''
  log.database:
    LEVEL: ''
    DRIVER: ''
    CONN: ''
  git:
    MAX_GIT_DIFF_LINES: 10000
    GC_ARGS: ''
  git.fsck:
    ENABLE: true
    INTERVAL: 24
    ARGS: ''
  i18n:
    LANGS: 'en-US'
    NAMES: 'English'


```


```YAML


     - {
         role: "sa-gogs",
         gogs_app_ini: "{{gogs_custom_app_ini}}"
       }

```


Usage with ansible galaxy workflow
----------------------------------

If you installed the sa-gogs role using the command


`
   ansible-galaxy install softasap.sa-gogs
`

the role will be available in the folder library/softasap.sa-gogs
Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-gogs"
       }

```



Copyright and license
---------------------


Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
