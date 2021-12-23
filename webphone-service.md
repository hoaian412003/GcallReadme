# GCALLS COMMUNITY - WEBPHONE SERVICE

<p align="center"><img src="sources/images/callbox.png"></p>

***

Webphone service is an web application that is a main UI of this project. It allow callcenter agent manages contacts. Webphone also helps agents grow up their customer support service quality. Webphone provides callbox, intergrating CRM... 

### Prerequisites

***

* Redis:
    - Store user's session. Even if the server has shutdown accidently, the session is still kept.
    - [Website](https://redis.io/)
* PM2:
    - Only for development and production environment.
    - is a production process manager for Node.js applications with a built-in load balancer. It allows you to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks.
    - Major feature set:
        + Process management including automatic app restarts on failure or system reboots
        + Application monitoring
        + Declarative configuration via JSON file
        + Log management
        + Built-in cluster mode
        + Startup script generation for *nix systems
        + Seamless updates
        + Integrated module system
    - [Github repo](https://github.com/Unitech/pm2)

### Features
***
- Admin
    + Manage contacts and contact group
    + Manage call logs and activities
    + Manage user
    + Manage SIP providers
    + Manage roles
    + Statistics
- Agent
    + Call box
    + Send SMS
    + Add tag call log
    + Add note contact
    + Manage contact and contact group
    + Listen record call log
    + View history call logs and activities

### Installation

***

* Install Redis: [Instruction link](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04)

* Clone project:

~~~
git clone https://gitlab.com/gcalls-opensource/gcalls-community-version.git
~~~

* Change dir into webphone-service folder

~~~
cd webphone-service
~~~

* Install utility modules:

~~~
npm install
~~~

* Start server:
    * run in development

    ~~~    
    npm run dev
    ~~~

    * run in production
    
    ~~~
    npm install -g pm2
    npm start
    ~~~

### Source tree
***
~~~
├───client/
│   ├───Admin/
│   │   ├───actions/
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───Role.js
│   │   │   ├───SipAccount.js
│   │   │   ├───Statistics.js
│   │   │   └───User.js
│   │   ├───components/
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───Main.js
│   │   │   ├───Menu.js
│   │   │   ├───Navigation.js
│   │   │   ├───Role.js
│   │   │   ├───SecondaryLogTable.js
│   │   │   ├───SipAccount.js
│   │   │   └───Statistics.js
│   │   ├───constants/
│   │   │   ├───Agent.js
│   │   │   ├───Blacklist.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───ClickToCall.js
│   │   │   ├───Role.js
│   │   │   ├───Setup.js
│   │   │   ├───SipAccount.js
│   │   │   ├───Statistics.js
│   │   │   └───User.js
│   │   ├───locales/
│   │   │   ├───en.js
│   │   │   ├───index.js
│   │   │   └───vi.js
│   │   ├───reducers/
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───Role.js
│   │   │   ├───SipAccount.js
│   │   │   ├───Statistics.js
│   │   │   ├───User.js
│   │   │   └───index.js
│   │   ├───socket.io/
│   │   │   └───index.js
│   │   ├───app.js
│   │   └───store.js
│   ├───Agent/
│   │   ├───actions/
│   │   │   ├───Activity.js
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───Contact.js
│   │   │   ├───ContactGroup.js
│   │   │   ├───User.js
│   │   │   └───integration.js
│   │   ├───components/
│   │   │   ├───Activity.js
│   │   │   ├───CallBox.js
│   │   │   ├───Contact.js
│   │   │   ├───ContactGroup.js
│   │   │   ├───IndexPage.js
│   │   │   ├───Main.js
│   │   │   ├───Modal-SMS-Group.js
│   │   │   ├───Modal-SMS.js
│   │   │   ├───Notification.js
│   │   │   ├───historyCalllog.js
│   │   │   └───listenRecord.js
│   │   ├───constants/
│   │   │   ├───Activity.js
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───Contact.js
│   │   │   ├───ContactGroup.js
│   │   │   ├───FAQ.js
│   │   │   ├───FAQrequested.js
│   │   │   ├───FAQtag.js
│   │   │   └───User.js
│   │   ├───locales/
│   │   │   ├───en.js
│   │   │   ├───index.js
│   │   │   └───vi.js
│   │   ├───reducers/
│   │   │   ├───Activity.js
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───CheckNetwork.js
│   │   │   ├───Contact.js
│   │   │   ├───ContactGroup.js
│   │   │   ├───User.js
│   │   │   └───index.js
│   │   ├───socket.io/
│   │   │   ├───Contact.js
│   │   │   ├───Notification.js
│   │   │   ├───User.js
│   │   │   └───index.js
│   │   ├───app.js
│   │   ├───function.js
│   │   └───store.js
│   ├───Anonymous/
│   │   ├───components/
│   │   │   ├───Confirm.js
│   │   │   ├───ForgetPassword.js
│   │   │   ├───Main.js
│   │   │   ├───SignIn.js
│   │   │   └───SignUp.js
│   │   ├───locales/
│   │   │   ├───en.js
│   │   │   ├───index.js
│   │   │   └───vi.js
│   │   ├───redux/
│   │   │   └───store.js
│   │   └───app.js
│   ├───config/
│   │   └───record.js
│   └───library/
│       └───debug.js
├───jsonwebtoken/
│   └───index.js
├───public/
│   ├───aehlke-tag-it/
│   ├───css/
│   ├───fonts/
│   ├───img/
│   ├───js/
│   ├───sounds/
├───rabbitMQ/
│   ├───client/
│   │   └───user.js
│   ├───config/
│   │   ├───connect.js
│   │   └───host.json
│   └───server/
│       └───user.js
├───server/
│   ├───config/
│   │   ├───access.js
│   │   ├───aws.js
│   │   ├───feature.js
│   │   ├───host.js
│   │   ├───integration.js
│   │   ├───jwt.js
│   │   ├───log-service.js
│   │   ├───mailer.js
│   │   ├───mapper.js
│   │   └───redis.js
│   ├───lib/
│   │   ├───access.js
│   │   ├───email.js
│   │   ├───feature.js
│   │   ├───integration.js
│   │   ├───jwt.js
│   │   ├───logger.js
│   │   ├───password.js
│   │   ├───phonenumber.js
│   │   └───pubsub.js
│   ├───middleware/
│   │   └───authenticate.js
│   ├───route/
│   │   ├───authenticated/
│   │   │   ├───Activity.js
│   │   │   ├───Agent.js
│   │   │   ├───CallLog.js
│   │   │   ├───Contact.js
│   │   │   ├───ContactField.js
│   │   │   ├───ContactGroup.js
│   │   │   ├───Integration.js
│   │   │   ├───Invite.js
│   │   │   ├───Log.js
│   │   │   ├───Record.js
│   │   │   ├───SipAccount.js
│   │   │   ├───Template.js
│   │   │   └───User.js
│   │   ├───unauthenticated/
│   │   │   ├───ForgetPassword.js
│   │   │   ├───Invite.js
│   │   │   ├───Notify.js
│   │   │   └───User.js
│   │   └───index.js
│   └───views/
│       ├───admin.html
│       ├───agent.html
│       ├───non-user.html
│       └───robots.txt
├───sources/
│   ├───images/
│   │   └───callbox.png
│   └───api.yaml
├───.babelrc
├───.gitlab-ci.yml
├───Dockerfile
├───README.md
├───index.js
├───package.json
├───server.js
├───webpack.common.js
├───webpack.config.js
├───webpack.dev.js
├───webpack.prod.js

~~~
***
### Utility modules

***

* __Express__ - Node.js web application framework: <http://expressjs.com/>
* __Babel__ - is a community-driven tool that helps you write code in the latest version of JavaScript: <https://github.com/babel/babel>
* __Axios__ - Promise based HTTP client: <https://github.com/mzabriskie/axios>
* __Redis__ - connect-redis is a Redis session store backed by node_redis: <https://github.com/tj/connect-redis>
* __React__ - a javascript framework for building user interface: <https://facebook.github.io/react/>
* __React Router__ - is a complete routing library for React, keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling built right in. Make the URL your first thought, not an after-thought: <https://github.com/ReactTraining/react-router/tree/v3.0.5>
* __Redux__ - is a predictable state container for JavaScript apps: <https://github.com/reactjs/redux>
* __Redux thunk__ - Redux Thunk middleware allows you to write action creators that return a function instead of an action:  <https://github.com/reduxjs/redux-thunk>
* __Webpack__ - is a module bundler. Its main purpose is to bundle JavaScript files for usage in a browser, yet it is also capable of transforming, bundling, or packaging just about any resource or asset: <https://github.com/webpack/webpack>
* __Winston__ - is designed to be a simple and universal logging library with support for multiple transports. A transport is essentially a storage device for your logs. Each instance of a winston logger can have multiple transports configured at different levels: <https://github.com/winstonjs/winston>
* __Morgan__ - HTTP request logger middleware for node.js: <https://github.com/expressjs/morgan>
* __connect-multiparty__ - Parse http requests with content-type multipart/form-data: <https://github.com/expressjs/connect-multiparty>
* __Aws sdk__ - The official AWS SDK for JavaScript, available for browsers and mobile devices, or Node.js backend:  <https://github.com/aws/aws-sdk-js>


### Nginx config

***

* development

```
server {
	listen 80;
	listen [::]:80 default_server ipv6only=on;
	return 301 https://$host$request_uri;
}
server {
    listen 443;
    server_name <domain webphone-service>;

    ssl on;
    # Use certificate and key provided by Let's Encrypt:
    ssl_certificate /etc/tls/gcall.vn_ca.crt;
    ssl_certificate_key /etc/tls/gcall.vn.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH';

	add_header X-Frame-Options "SAMEORIGIN";

	location /record/ {
        proxy_pass              "<domain record-service>";
    }

    location / {
        proxy_set_header        X-Real-IP $remote_addr;
        proxy_set_header        X-Forwarded-For $remote_addr;
        proxy_set_header        Host $http_host;
        proxy_pass              "http://127.0.0.1:4004";
    }
	
	location /ws {
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header Host $http_host;
		proxy_set_header X-NginX-Proxy true;

		proxy_pass http://localhost:2893/ws;
		proxy_redirect off;
		
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection "upgrade";
	}
	
	location /assets/ {
        add_header 'Access-Control-Allow-Origin' '<domain webphone-service>';
		add_header Last-Modified $date_gmt;
		add_header Cache-Control 'no-store, no-cache, must-revalidate, proxy-revalidate, max-age=0';
        if_modified_since off;
		expires off;
		etag off;
		alias /home/ubuntu/webphone-service/public/;
    }
}
```

* production

```
server {
	listen 80;
	listen [::]:80 default_server ipv6only=on;
	return 301 https://$host$request_uri;
}
server {
	listen 443;
    server_name <domain webphone-service>;

    ssl on;
    # Use certificate and key provided by Let's Encrypt:
    ssl_certificate     /home/ubuntu/gcall-ssl/gcalls.co_ca.crt;
    ssl_certificate_key /home/ubuntu/gcall-ssl/gcalls.co.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH';

	add_header X-Frame-Options "DENY";

	location /record/ {
        proxy_pass              "<domain record-service>";
    }

    location / {
        proxy_set_header        X-Real-IP $remote_addr;
        proxy_set_header        X-Forwarded-For $remote_addr;
        proxy_set_header        Host $http_host;
		proxy_pass              "http://127.0.0.1:4004";
	}
	
	location /ws {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-NginX-Proxy true;

        proxy_pass http://localhost:2893/ws;
        proxy_redirect off;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
	
	location /assets/ {
        add_header 'Access-Control-Allow-Origin' '<domain webphone-service>';
		add_header Cache-Control no-cache;
        alias /home/ubuntu/webphone-service/public/;
    }
}
```
### API

> All APIs in [api.yaml](sources/api.yaml). Use [Swagger Editor](http://editor.swagger.io) to view.

### Author

***
* __Duong Cat Hung Vuong__ <vuong.duong@gcalls.co>- Fullstack engineer at Gcall Vietnam Pte Ltd
* __Dang Hoang Thien__ <thien.dang@gcalls.co>- Frontend developer at Gcall Vietnam Pte Ltd
* __Vo Ngoc Mai Linh__ <linh.vo@gcalls.co> - Fullstack engineer at Gcall Vietnam Pte Ltd

### Acknowlegde

***
* This project is based on   __react@15.6.2__, __react-router@3__. There are many changes in __react-router@4__ and __react^@16__, it's not able to used in this project. Be careful if you want to upgrade version of these packages.


