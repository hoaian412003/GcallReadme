# GCALLS COMMUNITY - ACCESS SERVICE

***

Access service is a one of the main service of this project. This service is responsible for receiving requests from the above services such as webphone service, mobile service, ... and calling the below services such as user service, customer service, .. to perform the request, then return the results for the above services

### Technology

***

* Multi-tenancy:
    - is an architecture in which a single instance of a software application serves multiple customers. Each customer is called a tenant. Tenants may be given the ability to customize some parts of the application, such as color of the user interface (UI) or business rules, but they cannot customize the application's code.
    - Multi-tenancy can be economical because software development and maintenance costs are shared. It can be contrasted with single-tenancy, an architecture in which each customer has their own software instance and may be given access to code. With a multi-tenancy architecture, the provider only has to make updates once. With a single-tenancy architecture, the provider has to touch multiple instances of the software in order to make updates.
    - In cloud computing, the meaning of multi-tenancy architecture has broadened because of new service models that take advantage of virtualization and remote access. A software-as-a-service (SaaS) provider, for example, can run one instance of its application on one instance of a database and provide web access to multiple customers. In such a scenario, each tenant's data is isolated and remains invisible to other tenants.
* Basic authentication:
    - In the context of a HTTP transaction, basic access authentication is a method for a HTTP user agent to provide a user name and password when making a request.
    - HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it doesn't require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header, obviating the need for handshakes.
* RESTful API:
    - An architectural style called [REST (Representational State Transfer)](https://en.m.wikipedia.org/wiki/Representational_state_transfer) advocates that web applications should use HTTP as it was originally envisioned. Lookups should use __GET__ requests. __PUT__, __POST__, and __DELETE__ requests should be used for "mutation, creation, and deletion respectively".👩
    - Building RESTful web services, like other programming skills is part art, part science. As the Internet industry progresses, creating a REST API becomes more concrete with emerging best practices. As RESTful web services don't follow a prescribed standard except for HTTP, it's important to build your RESTful API in accordance with industry best practices to ease development and increase client adoption.
* Domain Driven Design (DDD): is an approach to software development for complex needs by connecting the implementation to an evolving model. The premise of domain-driven design is the following:
    - placing the project's primary focus on the core domain and domain logic.
    - basing complex designs on a model of the domain.🌏
    - initiating a creative collaboration between technical and domain experts to iteratively refine a conceptual model that addresses particular domain problems.
* HTTP protocol:
    - HTTP means _HyperText Transfer Protocol_. HTTP is the underlying protocol used by the World Wide Web and this protocol defines how messages are formatted and transmitted, and what actions Web servers and browsers should take in response to various commands.
    - HTTP is called a _stateless_ protocol because each command is executed independently, without any knowledge of the commands that came before it. This is the main reason that it is difficult to implement Web sites that react intelligently to user input. This shortcoming of HTTP is being addressed in a number of new technologies, including ActiveX, Java, JavaScript and cookies.
    - A similar abbreviation, _HTTPS_ means _Hyper Text Transfer Protocol Secure_. Basically, it is the secure version of HTTP. Communications between the browser and website are encrypted by Transport Layer Security (TLS), or its predecessor, Secure Sockets Layer (SSL).🎧

### Prerequisites

***

* Ubuntu:
    - is an open source operating system software for computers. It is one of the distribution systems of [Linux](https://en.wikipedia.org/wiki/Linux), and is based on the [Debian](https://en.wikipedia.org/wiki/Debian) architecture. Besides personal computers, Ubuntu is available for tablets and smartphones, with the Ubuntu Touch edition. It also runs network servers. That is usually with the Ubuntu Server edition, either on physical or virtual servers (such as on mainframes) or with containers, that is with enterprise-class features. It runs on the most popular architectures, including server-class ARM-based.
    - Ubuntu is published by Canonical Ltd, who offer commercial support. It is based on free software and named after the Southern African philosophy of ubuntu (literally, 'human-ness'), which Canonical Ltd. suggests can be loosely translated as "humanity to others" or "I am what I am because of who we all are".
    - Ubuntu is the most popular operating system running in hosted environments, so–called "clouds", as it is the most popular server [Linux distribution](https://en.wikipedia.org/wiki/Linux_distribution).
* npm:
    - is the package manager for JavaScript and the world’s largest software registry. Discover packages of reusable code — and assemble them in powerful new ways.🗑
    - The npm Registry is a public collection of packages of open-source code for Node.js, front-end web apps, mobile apps, robots, routers, and countless other needs of the JavaScript community.
    - npm is the command line client that allows developers to install and publish those packages.
    - Use npm to install, share, and distribute code; manage dependencies in your projects; and share & receive feedback with others.
* NodeJS:
    - is a JavaScript runtime built on [Chrome's V8 JavaScript](https://developers.google.com/v8/) engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, [npm](https://www.npmjs.com/), is the largest ecosystem of open source libraries in the world.
* Mongo:
    - is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas. MongoDB is developed by MongoDB Inc. and is free and open-source, published under a combination of the GNU Affero General Public License and the Apache License.🇻🇳
    - [Website](https://docs.mongodb.com/manual/)
    - Provide:
        + mongo Shell Edition
        + Python Edition
        + Java Edition
        + Ruby Edition
        + Node.JS Edition
        + C++ Edition
        + C# Edition
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

### Utility modules

***

* __Express__ - Node.js web application framework: <http://expressjs.com/>
* __Axios__ - Promise based HTTP client: <https://github.com/mzabriskie/axios>
* __Winston__ - is designed to be a simple and universal logging library with support for multiple transports. A transport is essentially a storage device for your logs. Each instance of a winston logger can have multiple transports configured at different levels: <https://github.com/winstonjs/winston>
* __ESLint__ - is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs. In many ways, it is similar to JSLint and JSHint with a few exceptions: <http://eslint.org/>
    - ESLint uses Espree for JavaScript parsing.
    - ESLint uses an AST to evaluate patterns in code.
    - ESLint is completely pluggable, every single rule is a plugin and you can add more at runtime.
* __Morgan__ - HTTP request logger middleware for node.js: <https://github.com/expressjs/morgan>
* __co__ - Generator based control flow goodness for nodejs and the browser, using promises, letting you write non-blocking code in a nice-ish way: <https://github.com/tj/co>
* __Shortid__ - creates amazingly short non-sequential url-friendly unique ids. Perfect for url shorteners, MongoDB and Redis ids, and any other id users might see: <https://github.com/dylang/shortid>
    - By default 7-14 url-friendly characters: A-Z, a-z, 0-9, _-
    - Non-sequential so they are not predictable.
    - Supports cluster (automatically), custom seeds, custom alphabet.
    - Can generate any number of ids without duplicates, even millions per day.
    - Perfect for games, especially if you are concerned about cheating so you don't want an easily guessable id.
    - Apps can be restarted any number of times without any chance of repeating an id.
    - Popular replacement for Mongo ID/Mongoose ID.
    - Works in Node, io.js, and web browsers.
    - Includes Mocha tests.
* __Nodemailer__ - is a module for Node.js applications to allow easy as cake email sending. __Features__: <https://github.com/nodemailer/nodemailer>
    - A single module with __zero dependencies__ – code is easily auditable, as there are no dark corners
    - Heavy focus on __security__, no-one likes [RCE vulnerabilities](https://thehackernews.com/2017/01/phpmailer-swiftmailer-zendmail.html)
    - __Unicode support__ to use any characters, including emoji 💪
    - __Windows support__ – you can install it with [npm](https://www.npmjs.com/package/nodemailer) on Windows just like any other module, there are no compiled dependencies. Use it hassle free from Azure or from your Windows box
    - Use __HTML content__, as well as __plain text__ alternative
    - Add [Attachments](https://nodemailer.com/message/attachments/) to messages
    - [Embedded](https://nodemailer.com/message/embedded-images/) image attachments for HTML content – your design does not get blocked
    - Secure email delivery using __TLS/STARTTLS__
    - Different [transport methods](https://nodemailer.com/transports/) in addition to the built-in [SMTP support](https://nodemailer.com/smtp/)
    - Sign messages with [DKIM](https://nodemailer.com/dkim/)
    - Custom [Plugin support](https://nodemailer.com/plugins/) for manipulating messages
    - Sane [OAuth2](https://nodemailer.com/smtp/oauth2/) authentication
    - [Proxies](https://nodemailer.com/smtp/proxies/) for SMTP connections
    - __ES6 code__ – no more unintentional memory leaks, due to hoisted var’s
* __MongoDB__ - The official MongoDB driver for Node.js. Provides a high-level API on top of mongodb-core that is meant for end users: <https://github.com/mongodb/node-mongodb-native>

### Installation

***

* Clone project:

~~~
git clone https://gitlab.com/gcalls-opensource/gcalls-community-version.git
~~~

* Change dir into access-service folder

~~~
cd access-service
~~~

* Install utility modules:

~~~
npm install
~~~

* Lint project

~~~
npm run lint
~~~

* Start server:
    * run local
    ~~~
    npm run local
    ~~~

    * run in development

    ~~~
    npm install -g pm2
    npm run dev
    ~~~

    * run in production
    
    ~~~
    npm install -g pm2
    npm start
    ~~~

* Test

    #### _Before test make sure you have mongo installed_

    * Test all
    
    ~~~
    npm test
    ~~~

    * Test model
    
    ~~~
    npm run test-model
    ~~~

    * Test entity
    
    ~~~
    npm run test-entity
    ~~~

    * Test library
    
    ~~~
    npm run test-lib
    ~~~

### Source tree

```diff
- Need to add folder template which have to file are getAction.js and teamplate.js
```

***

```
├───config/
│   ├───authorization.js
│   ├───host.js
│   ├───mailer.js
│   ├───mongo.js
│   ├───redis.js
│   └───services.js
├───entity/
│   ├───Agent.js
│   ├───Callcenter.js
│   ├───Confirm.js
│   ├───Flowid.js
│   ├───Notification.js
│   ├───Reminder.js
│   └───User.js
├───lib/
│   ├───integration/
│   │   ├───freshsales.js
│   │   └───hubspot.js
│   ├───template/   (updated)
│   │   ├───getAction.js    (updated)
│   │   └───teamplate.js    (updated)
│   ├───email.js
│   ├───feature.js
│   ├───logger.js
│   ├───password.js
│   ├───pubsub.js
│   ├───schedule.js
│   └───services.js
├───middleware/
│   └───authorization.js
├───model/
│   ├───Callcenter.js
│   ├───Confirm.js
│   ├───Flowid.js
│   ├───ForgetPassword.js
│   ├───Invite.js
│   ├───Notification.js
│   ├───Reminder.js
│   ├───SipAccountTracking.js
│   └───User.js
├───route/
│   ├───Activity.js
│   ├───Agent.js
│   ├───Callcenter.js
│   ├───Calllog.js
│   ├───ClickToCall.js
│   ├───Confirm.js
│   ├───Contact.js
│   ├───ContactField.js
│   ├───ContactGroup.js
│   ├───Domain.js
│   ├───ForgetPassword.js
│   ├───Fpt.js
│   ├───Hubspot.js
│   ├───Integrator.js
│   ├───Mio.js
│   ├───Nhanh.js
│   ├───Pbx.js
│   ├───Record.js
│   ├───Role.js
│   ├───Sapo.js
│   ├───SipAccount.js
│   ├───System.js
│   ├───Template.js
│   ├───User.js
│   └───Vietguy.js
├───sources/
│   ├───images/
│   │   ├───ERD.jpg
│   │   └───microservice-model.jpg
│   └───api.yaml
├───template/
│   ├───forget-password.html
│   ├───reminder.html
│   ├───shopify-revoke-sip.html
│   ├───signup-confirm-shopify.html
│   ├───signup-confirm.en.html
│   ├───signup-confirm.vi.html
│   ├───signup-invite.html
│   ├───signup-success-with-trial-sip.html
│   ├───signup-success-without-trial-sip.html
│   └───signup-success.html
├───test/
│   ├───entity/
│   │   ├───Agent.js
│   │   ├───Callcenter.js
│   │   ├───Confirm.js
│   │   └───User.js
│   ├───lib/
│   │   ├───email.js
│   │   └───password.js
│   └───model/
│       ├───Callcenter.js
│       ├───Confirm.js
│       ├───ForgetPassword.js
│       ├───Invite.js
│       └───User.js
├───.babelrc
├───.dockerignore
├───.eslintrc
├───.gitignore
├───.gitlab-ci.yml
├───Dockerfile
├───README.md
├───index.js
├───package-lock.json
├───package.json
├───server.js
└───yarn.lock
```

### Database

***

* The whole view of Gcalls ERD
<p><img src="sources/images/ERD.jpg" width="100%"></p>

* Tables' description of Access Service

##### Callcenter

`Callcenter` is the main table to determine tenant. Each tenant is a callcenter.

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| name | string | name of callcenter |
| level | string | the current package that callcenter owner choose to use, each package has its limit (agents, functions) |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

##### User

`User` stores user's credetials that user has signed up or invited. This determines which callcenter that user belong to.

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| fullName | string | display name of user |
| email | string | the email that user uses to authenticate |
| password | string | password user uses to authenticate their access. This is a hashed string |
| salt | string | this is used to hash user's password by algorithm SHA512 |
| idCallcenter | string | `_id` of callcenter that user belongs to |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

##### Confirm

`Confirm` is used to confirm user's signup, this will send a link to their email to make sure that email exists.

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| email | string | the email that user uses to sign up |
| token | string | token to validate user's signup |
| expiredAt | int64 | Timestamp for the token will expire. After expire time, document will be deleted |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

##### Invitation

`Invitation` is used to validate invited user, this will send a link to invited user's email to make sure that email exists.

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| email | string | invited user's email |
| token | string | token to validate invited user |
| idCallcenter | string | `_id` of callcenter |
| idSip | string | `_id` of SIP account that admin has assigned |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

##### ForgetPassword

`ForgetPassword` is used to help user has forgot password, this will send a link to their email to make sure that email exists in `User` table.

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| email | string | the email that user uses to sign up |
| token | string | token to validate user's signup |
| expiredAt | int64 | Timestamp for the token will expire. After expire time, document will be deleted |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

### Services Model

***

* This shows architecture of microservice and which database is included in each service
<p><img src="sources/images/microservice-model.jpg" width="100%"></p>

### API

***

> All implemented APIs are specified in [api.yaml](sources/api.yaml) file.😜 Use [Swagger Editor](http://editor.swagger.io) to see the content.

### Author

***

* __Duong Cat Hung Vuong__ <vuong.duong@gcalls.co>💣 - Fullstack engineer at Gcall Vietnam Pte Ltd

