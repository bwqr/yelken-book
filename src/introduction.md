# Yelken Book
> Note: This book is still in progress and many parts of it are missing.
> Missing parts will be added as its development continues and its features get stabilized.

Welcome to Yelken book, where you can find all the details about Yelken and its features.
Yelken describes itself as a *Secure by Design, Extendable, and Speedy Next-Generation Content Management System (CMS)*.
Similar to WordPress, it delivers a traditional CMS experience by serving both as a content repository (backend) for you and presentation layer (frontend) for your users.

Literary, Yelken is a Turkish noun that means **sail** in English (check out [TDK](https://sozluk.gov.tr/?ara=yelken) for its pronunciation).
It is free for everyone to use, and its source code is available on [GitHub](https://github.com/bwqr/yelken).
Yelken is still under heavy development and may contain bugs or missing some features, but it is ready for experiments starting from its first alpha release.
If you have not read the first alpha release announcement, you are highly encouraged to read it [here](https://bwqr.github.io/yelken-blog/first-announcement/).

## Goals

Contrary to other CMS solutions, Yelken has a few ambitious goals specified in its description.
Firstly, the *Secure by Design* goal has the highest priority in Yelken, meaning that a Yelken instance must sustain its functionality without disclosing any private information to the public.
Additionally, it must keep itself from being infected by malicious user input or malicious plugins.
Thanks to the immutable core of Yelken and layered additions on top of it, it is easy to roll back its original functionality.

To make Yelken *Extendable*, it utilizes [WebAssembly System Interface (WASI) Preview 2](https://github.com/WebAssembly/WASI/blob/main/wasip2/README.md).
Thanks to WebAssembly's sandboxed execution environment, plugins are only able to perform operations restricted by Yelken.
They also cannot change the behavior of Yelken once they are disabled.
Moreover, with the help of programming languages' support for WebAssembly, such as low-level languages C, C++, and Rust, or high-level languages Javascript and Python, plugins can be written in any of these languages.

Lastly, Yelken tries to be a *Speedy* CMS by requiring very low computing resources (CPU and memory mainly) and serving many requests concurrently and quickly.
Under the hood, Yelken uses [Rust](https://www.rust-lang.org/) programming language and libraries developed around it to achieve its goals.

As an addition on top of three goals, Yelken aims to keep its deployment easy.
It might need to have various adapters to fit into different environments.
For instance, to support server hostings where only PHP, Mysql, and Apache CGI applications are supported, Yelken can provide a FastCGI implementation and use Mysql database, instead of its preferred Postgresql, to run in those environments.

## Next Step

To get started with Yelken, you can continue with the [Getting Started](./getting-started) chapter.
It introduces [Playground](./getting-started/playground.md) that enables having a first experience with Yelken.
It also guides you through [Running Yelken](./getting-started/running-yelken.md) if you want to run Yelken on your local machine.

After you have a Yelken instance running at somewhere, you can start learning how to use it by following the [Features](./features) chapter.
Sections under this chapter explain each feature of Yelken in details.
Following the features, you can look at [Examples](./examples) chapter to understand possible ways to use the Yelken.

Once you decide to use Yelken in one of your website, you can check the [Deployments](./deployments) chapter to learn how to deploy Yelken to production. <!-- If you want to learn more about the Yelken's underlying architecture, [Architecture](./architecture) chapter is a good place to start. -->
Lastly, you can check out the [Contributing](./contributing) page if you want to make any kind of contribution to Yelken.


## Learn more
Here are a few links to check out more about Yelken:

* Website [yelken.io](https://yelken.io)
* Repository: [github.com/bwqr/yelken](https://github.com/bwqr/yelken)
* Blog: [blog.yelken.io](https://blog.yelken.io)
* Playground: [playground.yelken.io](https://playground.yelken.io)
* Examples: [github.com/bwqr/yelken/tree/main/examples](https://github.com/bwqr/yelken/tree/main/examples)
* Discord server: [discord.gg/D4bfHr8neh](https://discord.gg/D4bfHr8neh)
