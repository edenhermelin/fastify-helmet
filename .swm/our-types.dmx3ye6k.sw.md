---
title: our types
---
# Introduction

This document will walk you through the implementation of the "our types" feature. This feature is designed to enhance the security of our application by integrating the Helmet library with our Fastify server. Helmet is a middleware that helps secure Express applications by setting various HTTP headers. It's not a silver bullet, but it can help!

We will cover:

1. Why we chose to use Helmet and Fastify together.


1. How we defined the types for the FastifyHelmet plugin.


1. What the FastifyHelmetOptions type is and why we need it.

# Choosing Helmet and Fastify

Fastify is a highly efficient HTTP server framework. Helmet, on the other hand, is a collection of middleware functions to help secure Express-based applications. By combining these two, we can create a highly efficient and secure server. However, to ensure that these two libraries work seamlessly together, we need to define some custom types. This is where our code change comes in.

<SwmSnippet path="/types/index.d.ts" line="20">

---

Defining FastifyHelmet type

```typescript
type FastifyHelmet = FastifyPluginAsync<fastifyHelmet.FastifyHelmetOptions> & {
  contentSecurityPolicy: typeof contentSecurityPolicy;
};
```

---

</SwmSnippet>

In the types/index.d.ts file, we define a new type, FastifyHelmet. This type is a combination of FastifyPluginAsync and an object that contains a contentSecurityPolicy property. The FastifyPluginAsync type is a generic type from the Fastify library that represents an asynchronous Fastify plugin. The contentSecurityPolicy property is a function from the Helmet library that sets the Content-Security-Policy header to help prevent cross-site scripting (XSS) attacks and other cross-site injections.

<SwmSnippet path="/types/index.d.ts" line="30">

---

Defining FastifyHelmetOptions type

```typescript
  export type FastifyHelmetOptions = {
    enableCSPNonces?: boolean,
    global?: boolean;
  } & NonNullable<HelmetOptions>;
```

---

</SwmSnippet>

Next, we define another type, FastifyHelmetOptions. This type represents the options that can be passed to the FastifyHelmet plugin. It includes two optional properties: enableCSPNonces and global. The enableCSPNonces property is a boolean that, when true, enables the use of nonces in the Content-Security-Policy header. The global property is also a boolean that, when true, applies the Helmet middleware globally to all routes. The FastifyHelmetOptions type also extends the HelmetOptions type from the Helmet library, which includes all the standard options that can be passed to Helmet.

By defining these types, we ensure that our Fastify server and Helmet middleware can work together seamlessly, while also providing a clear and type-safe way to configure our Helmet middleware.

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBZmFzdGlmeS1oZWxtZXQlM0ElM0FlZGVuaGVybWVsaW4=" repo-name="fastify-helmet"><sup>Powered by [Swimm](https://swimm-web-app.web.app/)</sup></SwmMeta>
