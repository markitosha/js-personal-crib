# Event Loop

### What is the Event Loop
The Event Loop is the heart of JavaScript's asynchronicity, responsible for executing tasks, managing callback queues, and enforcing the run-to-completion rule. It maintains a queue of tasks and processes them sequentially, allowing JavaScript to manage synchronous and asynchronous operations.

Here's the generalized algorithm of the Event Loop:

1. Dequeue the next task from the macro task queue (like timers, I/O, user interaction, script, etc).
2. Execute the task.
3. If the task is an asynchronous function, push the function callback to the micro task queue (like promise callbacks, MutationObserver callbacks, etc) and continue with the next macro task.
4. Once all macro tasks have been processed, move onto the micro task queue. Handle all microtasks in the queue before proceeding.
5. Execute render updates, such as requestAnimationFrame callbacks.
6. Loop back to step one and repeat the process.

This simple algorithm allows JavaScript to effectively manage and handle both synchronous tasks and asynchronous callbacks.

### Microtasks
Microtasks are tasks that get executed right after the currently executing script and before any other tasks get processed. Promise callbacks, MutationObserver callbacks, and queueMicrotask() tasks are considered microtasks.

Here's an example of a Promise-based microtask:

```javascript
Promise.resolve()
  .then(() => console.log('Microtask 1'))
  .then(() => console.log('Microtask 2'));
console.log('Synchronous task');
```

The microtask queue processes all of its tasks once the currently running task is finished and before rendering updates happen.

### Macrotasks
Macrotasks encompass a wider range of tasks including I/O operations, timers, and UI rendering. Specifically, tasks like `setTimeout`, `setInterval`, and user interaction events are all examples of macrotasks.

Here's an example of a `setTimeout` based macrotask:

```javascript
console.log('Synchronous task');
setTimeout(() => console.log('Macrotask'), 0);
Promise.resolve().then(() => console.log('Microtask'));
```

The macrotask queue will process one task per loop iteration. This includes the execution of the task and rendering updates.

### Animation
JavaScript's `requestAnimationFrame` API provides a method to schedule a callback to be invoked before the next repaint or reflow. It's a part of the rendering phase of the Event Loop, where the browser decides whether it will update the UI.

Remember, due to the nature of JavaScript and the Event Loop, even though these phases and the types of tasks imply a certain order, certain operations can cause jumps between phases and tasks can be processed out of order under certain circumstances.
