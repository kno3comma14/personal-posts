# WASM PART II: Using Rust and ClojureScript
In the last [post](https://flexiana.com/2021/11/wasm-part-i-what-is-webassembly-reasons-to-take-it-seriously) we studied what is WebAssembly,
it's influence in the modern web development and we presented a simple demo using WAT to WASM compilation. 
In this post, we will sove a more complex problem using [Rust](https://www.rust-lang.org/) to WASM compilation.

## WAT is not enough! 
TODO: General explanation why WAT is not enough for big applications.

## What is Rust? Why so much love is coming from the community?
TODO: Explain what is Rust and why the comunity is giving so much love to it.

## TiedUp!
TiedUp is a simple game about guessing the missing last three characters of a word located in the right side and the initial
three characters of a word located in the left side. For example, if the right word is doc**tor** and the left word is
**tor**toise, these words are tied by the three characters **tor**.

In this sample project we will present to you three words loaded from an external file using rust, and we will receive this 
data calling the respective function from ClojureScript.

### ClojureScript - Presentation layer
Like we mentioned in the previous post [post](https://flexiana.com/2021/11/wasm-part-i-what-is-webassembly-reasons-to-take-it-seriously), we are fans of Clojure/Script so we will use ClojureScript
to present the game to our players. We are creating a simple GUI to present and control the user interaction with the game.

### Rust - Business layer
In the business layer we will be using [Rust](https://www.rust-lang.org/) to read a file of words, with this file we can pass the information to ClojureScript. This is a simple task but we want to illustrate here how is the interaction between
WASM  and ClojureScript in action.

### Integration - Business Layer <=> Presentation Layer
TODO: How to integrate both projects and how run the project

## Conclusion
TODO: Rephrase the whole article and give an approximation approach for future articles.

