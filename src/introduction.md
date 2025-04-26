# Yelken Book
> Note: This book is still in progress and many parts of it are missing.
> Missing parts will be added as its development continues and its features get stabilized.

Welcome to Yelken book, where you can find all the details about Yelken and its features.
Yelken describes itself as a *Secure by Design, Extendable, and Speedy Next-Generation Content Management System (CMS)*.
Similar to WordPress, it delivers a traditional CMS experience by serving both as a content repository (backend) for you and presentation layer (frontend) for your users.

Literary, Yelken is a Turkish noun that means **sail** in English.
It is free for everyone to use, and its source code is available on [Github](https://github.com/bwqr/yelken).
Yelken is still under heavy development and may contain bugs or missing some features, but it is ready for experiments starting from its first alpha release.
If you have not read the first alpha release announcement, you are highly encouraged to read it from [here](/announcement.md).

## Goals

Contrary to other CMS solutions, Yelken has a few ambitious goals specified in its description.
Firstly, *Secure by Design* goal has the highest priority in Yelken and means that a Yelken instance must sustain its functionality without disclosing any private information to public.
Additionally, it must keep itself from being infected by malicious user input or malicious plugin.
Thanks to immutable core of Yelken and layered additions on top of it, it is easy to rollback its original functionality.

To make Yelken *Extendable*, it utilizes [WebAssembly System Interface (WASI) Preview 2](https://github.com/WebAssembly/WASI/blob/main/wasip2/README.md).
Thanks to WebAssembly's sandboxed execution environment, plugins are only able to perform operations restricted by Yelken.
They also cannot change behavior of Yelken once they are disabled.
Moreover, with the help of programming languages' support for WebAssembly, such as low-level languages C, C++, and Rust, or high-level languages Javascript and Python, plugins can be written in any of these languages.

Lastly, Yelken tries to be a *Speedy* CMS by requiring very low computing resources (CPU and memory mainly) and serving many requests concurrently and quickly.
Under the hood, Yelken uses [Rust](https://www.rust-lang.org/) programming language and libraries developed around it to achieve its goals.

As an addition on top of three two goals, Yelken aims to keep its deployment easy.
It might need to have different adapters to fit into different environments and they can be provided within Yelken.
For instance, to support server hostings where only PHP, Mysql and CGI applications are supported, Yelken can provide a FastCGI implementation and use Mysql database, instead of its preferred Postgresql, to run in those environments.

## Next Step

To get started with Yelken and run it on your machine or deploy it to somewhere, you can continue with [Getting Started](/getting-started.md) chapter.
If you want to delve into its architecture and features, you can continue with [Architecture](/artchitecture.md) chapter.
