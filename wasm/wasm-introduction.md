# WASM Part I: What is WebAssembly? Reasons to take it seriously
This article is the beginning of a serie of two more posts that describes what is [WebAssembly(WASM)](https://webassembly.org/)
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
Having these ideas in consideration, [WebAssembly(AKA WASM)](https://webassembly.org/) was launched in 2017 as a [binary instruction format](https://webassembly.github.io/spec/core/binary/index.html)
for a **stack-based virtual machine**. We know this definition is almost the same shown at [webassembly.org](https://webassembly.org/)
so let extend a little bit more this explanation. Let's start with **binary instruction format**, this one is simple
because it represents the way [WASM](https://webassembly.org/) expose instructions to the computer in order to be processed. On
the other hand, we have a **stack-based virtual machine** which store the instructions from WASM files in memory
using a stack as a main structure(We will talk more about this later).
## Main goals of WebAssembly
Like any other technology in the web, WebAssembly has been created thinking about some specific goals in mind. We are
presenting these goals in a different as follows:
- Security: WebAssembly provides a secure sandboxed virtual machine. This means that we can WASM code from any web application
without thinking about intrusions over our personal computers or servers. Proof of this point is any of the most used browsers
in the web have its support enabled by default because they are confident about the security provided by WASM.
- Fast execution: WASM is compiled into a binary format that will be executed at low level. In this way we will deliver
near native performance execution times.
- Portability: Three of the promises of WASM are Hardware/Language/Platform independency. This principle implies portability
for this three different factors.
A valuable note for the reader could be a list of different languages that compile to WebAssembly, if you want this resource please
go to this [link](https://github.com/appcypher/awesome-wasm-langs)
## How WebAssembly works?
We already gave you a brief description of multiple aspects around WebAssembly, now we will explain how it works. First, we will introduce
the general process describing any step of the development life cycle.
After this explanation, we will show you all the development life cycle using two different practical examples:
1) Using wat => WASM, we will write some code using a textual representation named **wat** and will compile to WASM.
2) Using Rust => WASM, we will write some code using [Rust](https://www.rust-lang.org/) and will compile to WASM.
### General development life-cycle
The development life-cycle for any WASM application follows a common set of steps. In the following lines we will mention
and explain every step of this process.
1) Source code implementation: For the implementation of the source code we can select any language that will be available
to compile to WASM.
2) Compilation phase: We will compile the source code to WASM using a compiler such as [Emscripten](https://emscripten.org/) or [Cheerp](https://leaningtech.com/cheerp/).TODO: Complete this process with the queue machine working example
3) Execution phase: The execution phase will run **wasm** extention files as binaries. 
### Time to practice!
We presented you a brief introduction to WebAssembly, how it works and the general development life cycle. Now it's time
to all this stuff in practice. Let's start with our first example: **Wat to WASM!**
### Wat to WASM!
In this example we will be using the WASM textual representation known as **Wat**. With this format, the code can be read
by humans but it's not the best option for larger applications. With this example we want to show you that **WASM** applications
could be made even without a sophisticated setup or any famous programming language existent our there.
#### Setup
First of all we will need [CMake](https://cmake.org/) because it is a pre-requisite to install [The WebAssembly Binary Toolkit or WABT](https://github.com/webassembly/wabt). In
MacOS is easy to install, we just need to run ```brew install cmake``` and wait for the instalation to be completed. In linux [CMake](https://cmake.org/) probably
will exists in many different package managers so it could be something like ```sudo apt-get install cmake``` for debian/ubuntu users or the substitution of ```apt-get```
by any of your package managers. For windows users, please follow these [instructions](https://cmake.org/install/).
After the instalation of CMake we will need to install [The WebAssembly Binary Toolkit or WABT](https://github.com/webassembly/wabt). In order to do this,
we need to clone the git repository using the following commands:
1) ```git clone --recursive https://github.com/WebAssembly/wabt```
2) ```cd wabt```
3) ```git submodule update --init```
[WABT](https://github.com/webassembly/wabt) needs to use several submodules for some tests, that's the reason we are initializing and updating the submodules.

Now, we need to run the following instructions in order to build [WABT](https://github.com/webassembly/wabt):
1) ```mkdir build```
2) ```cd build```
3) ```cmake ..```
4) ```cmake .```

After this step we recommend you to add the route for the ```bin``` folder to the ```$PATH```, in this way you don't have to put
the complete path to ```bin``` everytime you want to execute every [WABT](https://github.com/webassembly/wabt) command.
#### Time to code
Perfect, we have completed the setup, so now it's time to create our first *.wat file, compile it to a *.wasm file and call it from Javascript.
First of all, create a project folder using the following command:
```mkdir my_first_project```
or you can use your favorite editor for this purpose as well. Inside this folder we need to create a wat file using our editor or this command:
```touch add.wat```
### Rust to WASM!
TODO: Expose example to be executed using Rust.
## Conclusion
In this article we talked about [WebAssembly](https://webassembly.org/) and explored the basic concepts and pilars
of this amazing technology. In the next part of this series of articles we will take these concepts to the practice.

Enyert Vinas is a software engineer at Flexiana(Using Clojure, Python and other languages as his toolchain), game developer and
musician. He is living in Medellin, Colombia.
