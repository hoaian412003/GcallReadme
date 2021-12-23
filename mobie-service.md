# GCALLS COMMUNITY - MOBILE SERVICE

***
Mobile service is the service backend for extension integration such as hubspot. It has a backend similar to a webphone service

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
* Manage activity
* Manage agent
* Manage call log
* Manage contact
* Manage contact group
* Manage integration
* Manage template sms
### Installation

***

* Clone project:

~~~
git clone https://gitlab.com/gcalls-opensource/gcalls-community-version.git
~~~

* Change dir into mobile-service folder to run backend

~~~
cd mobile-service
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

```diff
-   Need add file logger.js in folder config
-   Need add file package-lock.json in folder /
```

```
├───config/
│   ├───access.js
│   ├───host.js
│   ├───integration.js
│   ├───jwt.js
│   ├───mongodb.js
│   ├───redis.js
│   └───webphone.js
│   └───logger.js   (updated)
├───lib/
│   ├───access.js
│   ├───integration.js
│   ├───pubsub.js
│   └───validate.js
├───middleware/
│   ├───auth.js
│   └───integration.js
├───route/
│   ├───activity.js
│   ├───agent.js
│   ├───call_log.js
│   ├───contact.js
│   ├───contact_field.js
│   ├───contact_group.js
│   ├───integration.js
│   ├───session.js
│   └───template.js
├───.babelrc
├───.dockerignore
├───.gitignore
├───.gitlab-ci.yml
├───Dockerfile
├───README.MD
├───api.yaml
├───app.js
├───index.js
├───package.json
├───package-lock.json   (updated)
└───yarn.lock
```

