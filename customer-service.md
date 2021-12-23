# GCALLS COMMUNITY - CUSTOMER SERVICE

***
Customer Service is a service that manipulate database and can be accessed by Gateway via REST API. It only communicates with the access-service. A username and a password, exemplifying Basic Access Authentication, must be validated. This service stores customer information such as phone number, customer information, activities on the system.
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

* Create, store, and manipulate `Activity`: calllog, send sms,...
* Create, store, and manipulate `ContactGroup`: Contact information in a group
* Create, store, and manipulate `Contact`: Information of contact
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
* Bluebird - A full featured promise library with unmatched performance: <http://bluebirdjs.com/docs/getting-started.html>

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
* Change dir into customer-service folder

~~~
cd customer-service
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

***

```
├───config/
│   ├───auth.js
│   └───mongodb.js
├───lib/
│   └───middleware.js
├───model/
│   ├───activity.js
│   ├───activity_tag.js
│   ├───agentgroup.js
│   ├───call_log.js
│   ├───contact-and-group.js
│   ├───contact-group.js
│   ├───contact.js
│   ├───contact_field.js
│   └───template.js
├───route/
│   ├───activity.js
│   ├───agentgroup.js
│   ├───call_log.js
│   ├───contact-group.js
│   ├───contact.js
│   ├───contact_field.js
│   └───template.js
├───test/
│   ├───model/
│   │   ├───activity.test.js
│   │   ├───activity_tag.test.js
│   │   ├───agentgroup.test.js
│   │   ├───call_log.test.js
│   │   ├───contact-and-group.test.js
│   │   ├───contact-group.test.js
│   │   ├───contact.test.js
│   │   ├───contact_field.test.js
│   │   └───template.test.js
│   └───route/
│       ├───activity.test.js
│       ├───call_log.test.js
│       ├───contact-group.test.js
│       ├───contact.test.js
│       ├───contact_field.test.js
│       └───template.test.js
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
├───package.json

```

### Database schema

***

![Database schema](https://i.imgur.com/2uVE0YS.png)

##### Activity

`Activity` of an agent goes along with a contact. Indeed, every call center has a distinct collection to store their call logs. The collection names follow the format `activity_idCallcenter`

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| creator | string | `_id` of the agent creating the activity |
| idContact | string | `_id` of the contact involved |
| text | string | Description of the activity |
| type | string | Three accepted values of activity category are `note`, `calllog`, and `reminder` |
| body | object | If type is `calllog`, `body` includes `idCalllog`, `status`, `duration`, `direction`, `source`, `destination`, `start`, and `end`. If type is `reminder`, `body` includes `remindedAgent`, `duedate`, and `status` |
| body.status | string | If type is `calllog`, five accepted values are `success`, `missed`, `rejected`, `busy`, and `connected`. If type is `reminder`, two accepted values are `checked` and `unchecked` |
| body.idCalllog | string | `_id` of the call |
| body.duration | number | Length of call, measured in seconds |
| body.direction | string | Direction of the call, two accepted values are `incoming` and `outgoing` |
| body.source | string | Caller of the call |
| body.destination | string | Recipient of the call |
| body.start | number | Timestamp of the call initiation, in number of milliseconds since Unix epoch |
| body.end | number | Timestamp of the call end, in number of milliseconds since Unix epoch |
| body.remindedAgent | string | `_id` of agent reminded |
| body.duedate | number | Timestamp of the deadline on schedule, in number of milliseconds since Unix epoch |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |
| deleted | boolean | Status of visibility |

##### ContactGroup

`ContactGroup` provides information about a group of contacts chosen by an agent individually in their view. Indeed, every call center has a distinct collection to store their groups. The collection names follow the format `contactGroup_idCallcenter`

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| name | string | Name of the group |
| description | string | Description of the group |
| creator | string | `_id` of the agent creating the group |
| contactList | array | Each item is the `_id` of agent in the group |
| createdAt | int64 | Timestamp of the document creation, in number of milliseconds since Unix epoch |
| updatedAt | int64 | Timestamp of the last update, in number of milliseconds since Unix epoch |
| deleted | boolean | Status of visibility |

##### Contact

`Contact` provides information of a contact. Indeed, every call center has a distinct collection to store their contacts. The collection names follow the format `contact_idCallcenter`

| Field | Type | Description |
|:-----|:------|:-----------|
| _id | string | Unique identity string |
| firstName | string | First name of the contact |
| lastName | string | Last name of the contact |
| gender | string | Gender of the contact |
| email | string | Email of the contact |
| phone | string | Phone number of the contact |
| avatar | string | Avatar of the contact |
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

* `level`: There are 5 available levels provided by winston. This logger only uses `“error”` and `“info”`
* `timestamp`: The timestamp when log is created, in ISO format (`YYYY-MM-DDThh:mm:ss.sTZD`, for example, `"2017-10-09T03:34:22.359Z"`)
* `message`: A string (if logged by morgan) or a JSON object describing log content in details

##### Message

Each HTTP request generates these log messages with fields / values:

1. Request headers:
* `Authorization`: Includes token used for Basic Authentication protocol
2. Request body: Possesses same fields and values of request body
3. Database manipulation:
* `action`: 4 available values are `CREATE`, `READ`, `UPDATE`, and `DELETE`
* `table`: Name of the Mongo collection on which the query is applied
* `data`: A JSON object or an array of JSON objects, each may be:
    * The document which has just been inserted into collection
    * The result of finding query
    * The document which has just been successfully updated, with its new value
    * The document which has just been deleted
4. Error: Depending on kind of the error, it has a variety of subfields
5. Response error: If a technical or logical error occurs before, the request’s response will have error status code and message:
* `success`: `false`
* `message`: Description of the error
6. Information of request and response measured by `morgan`: A `string` that follows `short` format of `morgan`
`:remote-addr :remote-user :method :url HTTP/:http-version :status :res[content-length] - :response-time ms`

### Author

***

Nguyen The Hien <hien.nguyen@gcalls.co> - Backend developer at Gcall Vietnam Pte Ltd

### Acknowledgements

***

