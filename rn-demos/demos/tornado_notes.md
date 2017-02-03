# Tornado Notes

## 4 basic parts

- web framework (including `RequestHandler` which is subclassed to create web applications, and various supporting classes)
- Client- and server-side implementions of HTTP (`HTTPServer` and `AsyncHTTPClient`)
- An asynchronous networking library including the classes `IOLoop` and `IOStream`,which serve as the building
 blocks for the HTTP components
- A coroutine library (`tornado.gen`) which allows asynchronous code to be written in a more straightforward way than chaining callbacks.

Tornado is an alternative to WSGI

## Single threaded event loop

Application code should strive to be asynchronous
and non-blocking.

Only one operation can be active at a time.

Blocks - waits for something to happen before returning i/o or cpu

Asynchronous - returns before it is finished
- Callback argument
- return a placeholder (Future, Promise, Deferred)
- Deliver to a queue
- Callback registry (POSIX signals)

## Coroutines

Use the Python `yield` to suspend/resume execution

- Use `@gen.coroutine`
- create an http client async class
- yield while client fetches a url

Benefit - less places that a context switch can happen

## async and await

With Python 3.5 and Tornado 4.3+

`async def` instead of `@gen.coroutine`

`await` instead of `yield`