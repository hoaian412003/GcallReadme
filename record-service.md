# GCALLS COMMUNITY - RECORD SERVICE

***

This service is where to receive audio files from providers, store it to provide webphone-service and other services in the system.

### Prerequisites

***

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
* FFmpeg:
    - is the leading multimedia framework, able to decode, encode, transcode, mux, demux, stream, filter and play pretty much anything that humans and machines have created. It supports the most obscure ancient formats up to the cutting edge. No matter if they were designed by some standards committee, the community or a corporation. It is also highly portable: FFmpeg compiles, runs, and passes our testing infrastructure [FATE](http://fate.ffmpeg.org/) across Linux, Mac OS X, Microsoft Windows, the BSDs, Solaris, etc. under a wide variety of build environments, machine architectures, and configurations.
    - It contains libavcodec, libavutil, libavformat, libavfilter, libavdevice, libswscale and libswresample which can be used by applications. As well as ffmpeg, ffserver, ffplay and ffprobe which can be used by end users for transcoding, streaming and playing.
    - FFmpeg Tools:
        + [ffmpeg](http://www.ffmpeg.org/ffmpeg.html): A command line tool to convert multimedia files between formats
        + [ffserver](http://www.ffmpeg.org/ffserver.html): A multimedia streaming server for live broadcasts
        + [ffplay](http://www.ffmpeg.org/ffplay.html): A simple media player based on SDL and the FFmpeg libraries
        + [ffprobe](http://www.ffmpeg.org/ffprobe.html): A simple multimedia stream analyzer
    - FFmpeg Libraries for developers:
        + [libavutil](http://www.ffmpeg.org/libavutil.html) is a library containing functions for simplifying programming, including random number generators, data structures, mathematics routines, core multimedia utilities, and much more.
        + [libavcodec](http://www.ffmpeg.org/libavcodec.html) is a library containing decoders and encoders for audio/video codecs.
        + [libavformat](http://www.ffmpeg.org/libavformat.html) is a library containing demuxers and muxers for multimedia container formats.
        + [libavdevice](http://www.ffmpeg.org/libavdevice.html) is a library containing input and output devices for grabbing from and rendering to many common multimedia input/output software frameworks, including Video4Linux, Video4Linux2, VfW, and ALSA.
        + [libavfilter](http://www.ffmpeg.org/libavfilter.html) is a library containing media filters.
        + [libswscale](http://www.ffmpeg.org/libswscale.html) is a library performing highly optimized image scaling and color space/pixel format conversion operations.
        + [libswresample](http://www.ffmpeg.org/libswresample.html) is a library performing highly optimized audio resampling, rematrixing and sample format conversion operations.


### Feature
* Get records from providers and update record url in call log
* Store and provide record files for webphone service
### Installation

***

* Install FFmpeg:

~~~
// For Ubuntu 16.04
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ffmpeg
~~~

* Clone project:

~~~
git clone https://gitlab.com/gcalls-opensource/gcalls-community-version.git
~~~

* Change dir into record-service folder

~~~
cd record-service
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

### Features

***

* Store audio file recorded from webphone service

### Utility modules

***

* __Express__ - Node.js web application framework: <http://expressjs.com/>
* __Formidable__ - A Node.js module for parsing form data, especially file uploads: <https://github.com/felixge/node-formidable>
    * Fast (~500mb/sec), non-buffering multipart parser
    * Automatically writing file uploads to disk
    * Low memory footprint
    * Graceful error handling
    * Very high test coverage
* __Winston__ - is designed to be a simple and universal logging library with support for multiple transports. A transport is essentially a storage device for your logs. Each instance of a winston logger can have multiple transports configured at different levels: <https://github.com/winstonjs/winston>
* __Morgan__ - HTTP request logger middleware for node.js: <https://github.com/expressjs/morgan>
* __Body Parser__ - Node.js body parsing middleware. Parse incoming request bodies in a middleware before your handlers, available under the req.body property: <https://github.com/expressjs/body-parser>.
* __Fluent ffmpeg__ - abstracts the complex command-line usage of ffmpeg into a fluent, easy to use node.js module. In order to be able to use this module. fluent-ffmpeg requires ffmpeg >= 0.9 to work: <https://github.com/fluent-ffmpeg/node-fluent-ffmpeg>
### Source tree

```diff
- Need add file pbxlog.js in folder config
- Need add file package-lock.json in folder
```

***

```
├───config/
│   ├───access.js
│   ├───authorization.js
│   ├───aws.js
│   ├───credentials.js
│   ├───host.js
│   └───mongodb.js
│   └───pbxlog.js   (updated)
├───lib/
│   ├───access.js
│   ├───logger.js
│   ├───record.js
│   └───schedule.js
├───middleware/
│   └───authorization.js
├───model/
│   ├───domain.js
│   └───pbx.js
├───route/
│   ├───domain.js
│   ├───pbx.js
│   └───record.js
├───.babelrc
├───.dockerignore
├───.gitignore
├───.gitlab-ci.yml
├───API.md
├───Dockerfile
├───README.md
├───index.js
├───package.json
├───package-lock.json
└───server.js
```

### Author

***
* __Duong Cat Hung Vuong__ <vuong.duong@gcalls.co>💣 - Fullstack engineer at Gcall Vietnam Pte Ltd