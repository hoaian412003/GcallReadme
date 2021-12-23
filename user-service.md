
# GCALLS COMMUNITY - USER SERVICE

  

***

User Service is one of a service that manipulate database and can be accessed by Gateway via REST API. It only communicates with the access-service. A username and a password, exemplifying Basic Access Authentication, must be validated. This service stores user data, role data, sip account

### Technologies and techniques

  

***

  

* Multi-tenancy:

  

> The term "software multitenancy" refers to a software architecture in which a single instance of software runs on a server and serves multiple tenants. A tenant is a group of users who share a common access with specific privileges to the software instance. With a multitenant architecture, a software application is designed to provide every tenant a dedicated share of the instance - including its data, configuration, user management, tenant individual functionality and non-functional properties. Multitenancy contrasts with multi-instance architectures, where separate software instances operate on behalf of different tenants.

  

* MongoDB:

  

> MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

  

This service's database is organized in multi-tenancy, data belonging to each call center occupy a distinct MongoDB collection

  

* Basic Access Authentication:

  

> HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it doesn't require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header, obviating the need for handshakes.

  

All route handlers start with a middleware that validates `Bearer` token in `Authorization` field of header

  

* Unit testing:

  

> In computer programming, unit testing is a software testing method by which individual units of source code, sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures, are tested to determine whether they are fit for use.

  

All model functions and route handlers in this project undergo unit testing

  

* Test-driven development:

  

> Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: Requirements are turned into very specific test cases, then the software is improved to pass the new tests, only. This is opposed to software development that allows software to be added that is not proven to meet requirements.

  

* Continuous Integration & Deployment:

  

> Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily - leading to multiple integrations per day. Each integration is verified by an automated build (including test) to detect integration errors as quickly as possible. Many teams find that this approach leads to significantly reduced integration problems and allows a team to develop cohesive software more rapidly.

  

This repository utilizes GitLab CI/CD

  

> GitLab offers a continuous integration service. If you add a .gitlab-ci.yml file to the root directory of your repository, and configure your GitLab project to use a Runner, then each commit or push, triggers your CI pipeline.

  

### Features

  

***

  

* Create, store, and manipulate

*  `Agent`: this is where the user's information is stored in a callcenter

*  `Role`: By default, there are two roles: admin and agent. In addition, you can customize the role yourself

*  `SipAccount`: Save information about sip account from provider

* Authorize via a username and a password, exemplifying Basic Access Authentication

* Run unit testing all model functions and route handlers

* Log all requests and changes in database, rotating daily

  

### Packages

  

***

  

##### Application

  

* Express - Node.js web application framework: <http://expressjs.com/>

* MongoDB - Node.js Driver: <https://docs.mongodb.com/getting-started/node/client/>

* Dotenv - Storing configuration: <https://github.com/motdotla/dotenv>

* Body-parser - Node.js body parsing middleware: <https://github.com/expressjs/body-parser>

* Winston - A multi-transport async logging library for node.js: <https://github.com/winstonjs/winston>

* Winston-daily-rotate-file - A transport for winston which logs to a rotating file each day: https://github.com/winstonjs/winston-daily-rotate-file

* Morgan - HTTP request logger middleware for node.js: <https://github.com/expressjs/morgan>

  

##### Development

  

* Mocha - The fun, simple, flexible JavaScript test framework: <https://mochajs.org/>

* Chai - Assertion library for node: <https://github.com/chaijs/chai>

* Chai as Promised - Chai assertions for promises: <https://github.com/domenic/chai-as-promised>

* Chai HTTP - HTTP Response assertions for the Chai Assertion Library: <https://github.com/chaijs/chai-http>

* Istanbul - A JavaScript test coverage tool: <https://istanbul.js.org/>

* Nyc - Istanbul's state of the art command line interface: <https://github.com/istanbuljs/nyc>

* ESLint - The pluggable linting utility for JavaScript and JSX: <http://eslint.org/>

  

### Installation

  

***

  

* Clone project:

```

git clone https://gitlab.com/gcalls-opensource/gcalls-community-version.git

```

  

* Change dir into user-service folder

  

~~~

cd user-service

~~~

* Install packages:

```

npm install

```

  

* Start service:

* run in development

~~~

npm run dev

~~~

* run in production

~~~

npm install -g pm2

npm start

~~~

* Test service:

~~~

npm run test

~~~

  

### Source tree

```diff
- Need add file logger.js and file pbx.js in folder config
- Need add file package-log.json and file npm-debug.log in folder /
```

***

  

```

├───config/

│ ├───auth.js
│ ├───logger.js	(Updated)
│ ├───pbx.js	(Updated)

│ └───mongodb.js

├───lib/

│ └───middleware.js

├───model/

│ ├───agent.js

│ ├───role.js

│ └───sip_account.js

├───route/

│ ├───agent.js

│ ├───role.js

│ └───sip_account.js

├───test/

│ ├───model/

│ │ ├───agent.test.js

│ │ ├───role.test.js

│ │ └───sip_account.test.js

│ └───route/

│ ├───agent.test.js

│ ├───role.test.js

│ └───sip_account.test.js

├───.babelrc

├───.dockerignore

├───.eslintrc.js

├───.gitignore

├───.gitlab-ci.yml

├───Dockerfile

├───README.md

├───api.yaml

├───app.js

├───index.js

├───package-lock.json	(Updated)

├───npm-debug.log	(Updated)

└───package.json


  

```

  

### Database schema

  

***

  

![Database schema](https://i.imgur.com/9kGpFqV.png)

  

##### Agent

  

`Agent` is a person who works for a call center. Indeed, every call center has a distinct collection to store their agents. The table name follows the format `agent_idCallcenter`

  

| Field | Type | Description |

|:-----|:------|:-----------|

| _id | string | Unique identity string |

| role | string | Role assigned to the agent, two accepted values are `admin` and `agent` |

| idSip | string | `_id` of SIP account assigned to the agent |

| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |

| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

| deleted | boolean | Status of visibility |

  

##### Role

  

`Role` is assigned to each agent to determine their authorization. Indeed, every call center has a distinct table to store their roles. The table name follows the format `role_idCallcenter`

  

| Field | Type | Description |

|:-----|:------|:-----------|

| _id | string | Unique identity string |

| name | string | Name of the role, two accepted values are `admin` and `agent` |

| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |

| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

| deleted | boolean | Status of visibility |

  

##### SipAccount

  

A `SipAccount` provides authentication credentials to log in a SIP account. Indeed, every call center has a distinct table to store their SIP accounts. The table name follows the format `sipAccount_idCallcenter`

  

| Field | Type | Description |

|:-----|:------|:-----------|

| _id | string | Unique identity string, in this case, the hotline number |

| domain | string | Domain of the SIP account |

| extension | string | Number of extension in SIP URI |

| password | string | Password to get access to call connection |

| proxy| string | Proxy the of SIP account |

| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |

| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |

| deleted | boolean | Status of visibility |

  

### APIs

  

***

  

All implemented APIs are specified in `api.yaml` file in root folder of the project. Use [Swagger Editor](https://editor.swagger.io/) to see the content

  

### Logger

  

***

  

##### Location

  

All log files are stored in directory `log/process.env.NODE_ENV/` (root folder is the repository folder), for example, `log/production/`

  

Thanks to `winston-daily-rotate-file`, one log file is created each day with name format - `dd-MM-yyyy.winston`, for example, `09-10-2017.winston`

  

##### Entry

  

Each log entry is a JSON object, including:

  

*  `level`: There are 5 available levels provided by winston. This logger only uses `“error”` and `“info”`

*  `timestamp`: The timestamp when log is created, in ISO format (`YYYY-MM-DDThh:mm:ss.sTZD`, for example, `"2017-10-09T03:34:22.359Z"`)

*  `message`: A string (if logged by morgan) or a JSON object describing log content in details

  

##### Message

  

Each HTTP request generates these log messages with fields / values:

  

1. Request headers:

*  `Authorization`: Includes token used for Basic Authentication protocol

2. Request body: Possesses same fields and values of request body

3. Database manipulation:

*  `action`: 4 available values are `CREATE`, `READ`, `UPDATE`, and `DELETE`

*  `table`: Name of the Mongo collection on which the query is applied

*  `data`: A JSON object or an array of JSON objects, each may be:

* The document which has just been inserted into collection

* The result of finding query

* The document which has just been successfully updated, with its new value

* The document which has just been deleted

4. Error: Depending on kind of the error, it has a variety of subfields

5. Response error: If a technical or logical error occurs before, the request’s response will have error status code and message:

*  `success`: `false`

*  `message`: Description of the error

6. Information of request and response measured by `morgan`: A `string` that follows `short` format of `morgan`

`:remote-addr :remote-user :method :url HTTP/:http-version :status :res[content-length] - :response-time ms`

  

### Author

  

***

  

Nguyen The Hien <hien.nguyen@gcalls.co> - Backend developer at Gcall Vietnam Pte Ltd

  

### Acknowledgements

  

***