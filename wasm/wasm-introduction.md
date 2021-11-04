# WASM Part I: What is WebAssembly? Reasons to take it seriously
This article is the beginning of a serie of two more posts that describes what is WebAssembly(WASM)
and the importance of this technology. On completion, the reader should understand the basic
concepts related to this topic.
## The traditional web
The majority of the web is running using the traditional architecture, by traditional we mean
a web browser sending requests to a server via http/s. This web browser uses HTML and CSS to render 
content and delegate to JavaScript the responsibility to manage the behaviour of these components and the
interaction between the browser and the server via request - response life cycle. That's it, plain
and simple. 
## So, this scenario is working at the moment. What is the problem?
The problems with the traditional web are the limitations of the browser as interpreter/compiler(Depending
on the technology impemented by the browser) and rendered at the same time. In general, the performance of
JavaScript running resource-intensive applications like video editors, 3D games, and son on, is far away to
compete with the native performance.
## How to solve this problem? 
One of the many solutions for this problem could be the inclusion of a new lower level language with a compact
binary format to run alongside with JavaScript. In this way, we could use this language to develop near-native
performance features.
## WebAssembly, time to raise!
Having these ideas in consideration, WebAssembly(AKA WASM) was launched in 2017 as a [binary instruction format](https://webassembly.github.io/spec/core/binary/index.html)
for a **stack-based virtual machine**. We know this definition is almost the same shown at [webassembly.org](https://webassembly.org/)
so let extend a little bit more this explanation. Let's start with **binary instruction format**, this one is simple
because it represents the way [WASM](https://webassembly.org/) expose instructions to the computer in order to be processed. On
the other hand, we have a **stack-based virtual machine** which store the instructions from WASM files in memory
using a stack as a main structure(We will talk more about this later).
## Pillars of WebAssembly
TODO: Talk about the pillars of WebAssembly
## How WebAssembly works?
TODO: TODO Talk about how WASM works
## Conclusion
In this article we talked about [WebAssembly](https://webassembly.org/) and explored the basic concepts and pilars
of this amazing technology. In the next part of this series of articles we will take these concepts to the practice.

Enyert Vinas is a software engineer at Flexiana(Using Clojure, Python and other languages as his toolchain), game developer and
musician. He is living in Medellin, Colombia.
