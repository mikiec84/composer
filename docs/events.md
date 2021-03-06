[composer][] is an event emitter that may emit the following events:

### starting

This event is emitted when a `build` is starting.

The event emits 2 arguments, the current instance of [composer][] as the `app` and an object containing the build runtime information.

```js
app.on('starting', function(app, build) {});
```

* `build` exposes a `.date` object that has a `.start` property containing the start time as a `Date` object.
* `build` exposes a `.hr` object that has a `.start` property containing the start time as an `hrtime` array.

### finished

This event is emitted when a `build` has finished.

The event emits 2 arguments, the current instance of [composer][] as the `app` and an object containing the build runtime information.

```js
app.on('finished', function(app, build) {});
```

* `build` exposes a `.date` object that has `.start` and `.end` properties containing start and end times of the build as `Date` objects.
* `build` exposes a `.hr` object that has `.start`, `.end`, `.duration`, and `.diff` properties containing timing information calculated using `process.hrtime`

### error

This event is emitted when an error occurrs during a `build`.
The event emits 1 argument as an `Error` object containing additional information about the build and the task running when the error occurred.

```js
app.on('error', function(err) {});
```

Additional properties:

* `app`: current composer instance running the build
* `build`: current build runtime information
* `task`: current task instance running when the error occurred
* `run`: current task runtime information

### task:starting

This event is emitted when a task is starting.
The event emits 2 arguments, the current instance of the task object and an object containing the task runtime information.

```js
app.on('task:starting', function(task, run) {});
```

The `run` parameter exposes:

* `.date` **{Object}**: has a `.start` property containing the start time as a `Date` object.
* `.hr` **{Object}**: has a `.start` property containing the start time as an `hrtime` array.

### task:finished

This event is emitted when a task has finished.

The event emits 2 arguments, the current instance of the task object and an object containing the task runtime information.

```js
app.on('task:finished', function(task, run) {});
```

The `run` parameter exposes:

* `.date` **{Object}**: has a `.date` object that has `.start` and `.end` properties containing start and end times of the task as `Date` objects.
* `run` **{Object}**: has an `.hr` object that has `.start`, `.end`, `.duration`, and `.diff` properties containing timing information calculated using `process.hrtime`

### task:error

This event is emitted when an error occurrs while running a task.
The event emits 1 argument as an `Error` object containing additional information about the task running when the error occurred.

```js
app.on('task:error', function(err) {});
```

**Additional properties**

* `task`: current task instance running when the error occurred
* `run`: current task runtime information
