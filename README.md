# Koa Generic Session File store

This plugin for [koa-generic-session](https://github.com/koajs/generic-session)
is for when you just want basic file-based session stores. It's useful when you
want persistent sessions for a small number of users without having to spin up
an instance of Redis or Mongo.

## Installation

Install via npm:

```
npm install koa-generic-session-file
```

## Usage

Just plug it into koa-generic-session as you would with the other generic stores.
For example:

```js
var Koa = require("koa");
var session = require("koa-generic-session");
var FileStore = require("koa-generic-session-file");

var app = new Koa();
app.keys = ["keys", "keykeys"];

app.use(session({
  store: new FileStore()
}));
```

By default, the middleware will store session files in a directory called
"sessions" relative to your application's cwd. You can customise this path in
the options.

### Options

You can customise the behaviour of the store in a few small ways by passing
options in when instantiating FileStore:

- **sessionDirectory**: use this if you want to store your session files in
a custom location. It should be a path relative to your process.cwd() path,
or an absolute path.

```js
app.use(session({
  store: new FileStore({
    sessionDirectory: "/absolute/path/to/my/sessions"
  })
}));
```
