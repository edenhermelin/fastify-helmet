---
title: Update .taprc
---
# Introduction

This document will walk you through the implementation of the color change feature in the `.taprc` configuration file.

The feature was implemented to change the color scheme of the output from the TAP (Test Anything Protocol) utility. The color change was made to improve the readability and accessibility of the output, especially for developers with color vision deficiencies.

We will cover:

1. Why was the color change implemented?


1. How was the color change implemented?


1. What is the impact of this change on the overall application?

# Why was the color change implemented?

The color change was implemented to improve the readability of the output from the TAP utility. The previous color, yellow, was found to be difficult to read on certain backgrounds and for developers with certain types of color vision deficiencies. The new color, green, is generally easier to read and is more accessible.

# How was the color change implemented?

<SwmSnippet path="/.taprc" line="4">

---

The color change was implemented by modifying the .taprc configuration file. This file is used by the TAP utility to configure various aspects of its operation, including the color scheme of its output.

```
yellow: green
```

---

</SwmSnippet>

In this snippet, you can see that the color `yellow` has been changed to `green`. This change will affect all instances where the `yellow` color was previously used in the TAP output.

# What is the impact of this change on the overall application?

The impact of this change on the overall application is minimal. The change only affects the color scheme of the TAP output and does not affect the functionality of the application. However, the change does improve the readability and accessibility

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBZmFzdGlmeS1oZWxtZXQlM0ElM0FlZGVuaGVybWVsaW4="><sup>Powered by [Swimm](https://swimm-web-app.web.app/)</sup></SwmMeta>
