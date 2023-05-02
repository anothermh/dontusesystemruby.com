# Why not?

You're probably here because you asked someone for help with the version of [Ruby](https://www.ruby-lang.org/) that came pre-installed with your operating system. Your question was probably related to installing, uninstalling, downgrading, upgrading, configuring, or using that version of Ruby.

You were sent here so the person you asked doesn't have to take the time to answer your question, because the answer is:

> **Don't use system Ruby. Use a Ruby version manager to compile and install Ruby yourself because system Ruby is not meant to be used directly.**

# Why should I trust you?

I've been developing Ruby apps professionally since 2013, both as an individual contributor and as an organizational leader, at both some of the largest Ruby shops in the world (like [Yammer](https://github.com/yammer) and [New Relic](https://newrelic.com/ruby)) and at small startups. I've built multiple greenfield products from scratch using Ruby (and sometimes [Ruby on Rails](https://rubyonrails.org)) and have also developed new engineer onboarding guides multiple times. I'm also active on Stack Overflow's [ruby tag](https://stackoverflow.com/questions/tagged/ruby) where questions are commonly solved by using a Ruby manager.

But if you don't trust me you can always rely on the wisdom of others:

- [PSA: Do not use system Ruby](https://thoughtbot.com/blog/psa-do-not-use-system-ruby)
- [Why you shouldn't use the System Ruby](https://chrisherring.co/posts/why-you-shouldn-t-use-the-system-ruby)
- [Never Use System Ruby. Ever.](http://billpatrianakos.me/blog/2014/05/15/never-use-system-ruby-ever/)

# What is Ruby?

When programmers talk about Ruby they're really talking about two different things: [the programming language used to create Ruby apps](https://www.oreilly.com/library/view/the-ruby-programming/9780596516178/) and [the interpreter used to run Ruby apps](https://github.com/ruby/ruby).

## The Ruby language

The [Ruby](https://www.ruby-lang.org/) programming language is just like any other. Although there are important differences in how they work and are used, Ruby is comparable to [Python](https://python.org), [JavaScript](https://www.javascript.com), [PHP](https://www.php.net), [C](https://en.wikipedia.org/wiki/C_(programming_language)), [Swift](https://swift.org), [Rust](https://www.rust-lang.org), [Go](https://golang.org) ... you name it!

The Ruby language was created in 1993 by Yukihiro Matsumoto ("Matz") and the first version was released in 1996. It's an open-source, dynamic, object-oriented and interpreted language, widely regarded for its simplicity and elegance.

## The Ruby interpreter

The Ruby interpreter is a piece of software that reads and executes apps written in the Ruby language. Generally when speaking about the Ruby interpreter we're talking about [MRI](https://en.wikipedia.org/wiki/Ruby_MRI), also known as _Matz's Runtime Implementation_. This is the version of Ruby developed by the [Ruby maintainers](https://github.com/ruby/ruby/blob/master/doc/maintainers.rdoc), and accordingly is the first interpreter to support new features of the language.

There are other Ruby interpreters like [JRuby](https://www.jruby.org) and [TruffleRuby](https://github.com/oracle/truffleruby) but these are less popular and considered niche in the Ruby community. If someone is talking about MRI then they'll typically say _Ruby_ and if someone is talking about another interpreter then they'll call it by its proper name, like _JRuby_.

Unless you know that you specifically need an alternative Ruby interpreter it is recommended that you stick with MRI as it has the widest base of users.

# What is system Ruby?

> **Any version of Ruby that comes pre-installed with the operating system or is available as a package through the operating system's package manager is _system Ruby_.**

[Ruby](#the-ruby-interpreter) is freely available for anyone to use or modify, and it's possible to download its source code, compile it, and have it up and running on your computer in just a few minutes.

Since Ruby is available for free for commercial use, and since it is the version preferred by the core Ruby maintainers, and since it is the version the Ruby maintainers use to publish new features, Ruby is often bundled with operating systems like Linux and macOS. (some distributions of Linux may not include Ruby by default, but almost all will offer a package to install it)

Any version of Ruby that either came pre-installed with the operating system or can be downloaded using the operating system's package manager (like `sudo apt install ruby`) is what we call _system Ruby_.

# What is non-system Ruby?

Any version of Ruby that you download and compile yourself (either with a tool or by hand) qualifies as _non-system Ruby_. The easiest way to know the difference is if you download a package to install Ruby then you have _system Ruby_. (because the package manager knows your operating system version and your architecture and thus knows the pre-compiled Ruby package will run safely)

# Why not use system Ruby?

There are myriad reasons not to use system Ruby, and they all boil down to this simple reason:

!> **System Ruby belongs to the operating system and is not under your control.**

## System Ruby is meant to be used by the OS and its packages

When your operating system ships with Ruby, or when you install Ruby from your package manager, you are getting a version of Ruby that has been made to work within the narrow confines of what the operating system needs. That means Ruby will be installed in the directory it wants, with the configuration it wants, for the use-cases of either the operating system or packages that might depend on it.

Even though it's conveniently present it isn't there for you to use. It's there for the operating system and its packages _only_. The operating system doesn't care that you're using it and may make changes to it at any time.

The Ruby package isn't like a package for a calendar or mail app, which are meant to be used by you. The Ruby package is meant to be used by the operating system and other packages, and if it stops working properly then the operating system can and will happily stomp out any changes you've made to restore the system to a functioning state.

!> **System Ruby belongs to the operating system and is meant for use by the operating system and other packages, not by you.**

## System Ruby has restricted permissions

The filesystem on UNIX systems is protected by permissions. Certain directories and files have permissions that regular users on the system cannot change. Since the operating system wants to protect the tools that it relies on (like Ruby), the directories where Ruby is installed and where Ruby gems are installed have permissions that prevent users from making changes.

Of course, it's always possible to override this with `sudo` but when your operating system is telling you _don't touch these files_ it's a good idea to pay attention.

!> **System Ruby belongs to the operating system and may have filesystem permissions in place to prevent it from being used easily.**

## System Ruby is old

Most typically, the version of Ruby that ships with the system will be the version that was released when your operating system was released. Still running [Ubuntu 18.04 LTS](https://releases.ubuntu.com/18.04/)? Then [your system Ruby version is 2.5.1](https://packages.ubuntu.com/bionic/ruby), [released in 2018](https://www.ruby-lang.org/en/news/2018/03/28/ruby-2-5-1-released/).

Newer versions of Ruby will include bug fixes, security fixes, new features, and better performance. Additionally, new Ruby libraries may require newer versions of Ruby as they need new features of the language.

!> **System Ruby belongs to the operating system and will be locked at whatever version it needs, no matter how old, insecure, and unstable it may be.**

## System Ruby can't be upgraded

Did your operating system ship with Ruby 2.7 but you want to take advantage of the [new features of Ruby 3.0](https://www.ruby-lang.org/en/news/2020/12/25/ruby-3-0-0-released/)? Bad news, your operating system's maintainers haven't yet released (and maybe never will release) Ruby 3.0 as an update.

!> **System Ruby belongs to the operating system and its maintainers may not make newer versions available.**

## System Ruby can't be downgraded

Good news, your favorite operating system has released a new version! Bad news, it shipped with Ruby 3.0, there are no packages for Ruby 2.7, and all your apps and Ruby gems require Ruby 2.7!

!> **System Ruby belongs to the operating system and its maintainers may not make older versions available.**

## System Ruby can't be removed

If your operating system shipped with Ruby then chances are you can't remove it from your system. (an example of this is macOS) If you've modified (or damaged) your Ruby installation (and possibly left your operating system in an unstable state) then there may be no way to remove and reinstall Ruby — you have to reinstall the entire operating system.

!> **System Ruby belongs to the operating system and can't always be removed or repaired.**

## System Ruby can't coexist with other versions of Ruby

Your operating system will only allow you to have one version of Ruby installed: the version it chooses for you. If you need a different version than the one installed, say 1.9.3 instead of 2.7, you're out of luck.

!> **System Ruby belongs to the operating system and can't coexist with other versions.**

## System Ruby can change at any time

Even if you are able to use system Ruby successfully, there's no guarantee from the operating system that it won't modify, reset, or upgrade the version of Ruby present on the system. For example, when security updates for Ruby are released an updated version of system Ruby may be installed. The operating system has no way of knowing that you're using or have configured system Ruby and will happily overwrite the existing installation which can cause your Ruby apps to stop functioning.

!> **System Ruby belongs to the operating system and can change at any time.**

# Why have system Ruby at all?

When apps get deployed the servers they run on should be as simple and hardy as possible. [Docker containers](https://hub.docker.com/_/ruby), for example, are typically stripped down to the smallest size. In this type of environment it may be beneficial to use a prebuilt version of Ruby, either one that comes with the operating system or one installed through a package, because it may be undesirable to compile Ruby from scratch every time a new instance of the app is deployed.

These environments are more rigidly constructed and less prone to change than a device used for development.

Version managers are great tools for _development environments_ but not so much for _production environments_. If you're using a version manager in a production environment then you're probably doing something wrong.

# How do I install Ruby?

Ruby is easy to install using a version manager. A version manager is an application that will manage the installation and removal of Ruby versions on your device.

There are many benefits to using a version manager:

- Ruby will be downloaded fresh and compiled from scratch, ensuring it works best on your device
- Ruby will be installed to the directory of your choosing, typically somewhere in your home directory, making it both portable and entirely under your control
- Multiple versions of Ruby can be installed and used concurrently, from very old versions to the latest versions (including MRI, JRuby, TruffleRuby, and more)
- The operating system and its packages won't know about any Ruby installation done with a version manager, and thus can't interfere with it
- Each version of Ruby might require different steps to compile it from scratch but version managers maintain configurations for each version so they will always know how to install any given version — no fiddling with a `Makefile` required

## What version managers are there?

The version managers listed here are the most commonly used. There are other ways to install Ruby but for the vast majority of people the managers here are the primary ways to do it. You can always check [the Ruby installation instructions](https://www.ruby-lang.org/en/documentation/installation/) for an up-to-date list of possible version managers.

### asdf-vm

[asdf-vm](https://asdf-vm.com/#/core-manage-asdf) is a version manager built to support multiple tools, including Ruby, Java, node, Python, Go, [and many others](https://asdf-vm.com/#/plugins-all).

- This might be a good solution for you if you need to manage more than just Ruby.
- This might not be a good solution for you if you aren't familiar with the shell environment; it has a steeper learning curve than others and may require some hard-to-find documentation to get working. (but once you do, the knowledge will allow you to install and manage other tools easily)
- It has a large community for support.

### RVM

[RVM](http://rvm.io) is a version manager built specifically and only for Ruby. It's been around a long time and has a broad community of support.

- This might be a good solution for you if you only need to manage Ruby.
- This might not be a good solution for you if you have multiple other tools installed or a highly configured shell environment.

### chruby

[chruby](https://github.com/postmodern/chruby#readme) is a lot like rbenv but much lighter weight, and is built specifically and only for Ruby.

- This might be a good solution for you if you only need to manage Ruby, or if you don't need the configuration options provided by other version managers.
- This might not be a good solution for you if you aren't familiar with your shell environment and want the simplest, smallest manager available.

### rbenv

[rbenv](https://github.com/rbenv/rbenv#readme) is a lot like [asdf-vm](#asdf-vm) and works mostly in the same ways, but is built specifically and only for Ruby.

- This might be a good solution for you if you only need to manage Ruby, or if you're familiar with similar tools like [pyenv](https://github.com/pyenv/pyenv).
- This might not be a good solution for you if you have multiple other tools installed or a highly configured shell environment.

## What is the best version manager?

The version manager you choose will depend on your needs and your comfort level with the shell environment. Here are some things to consider:

- Do you need to manage more than just Ruby? (e.g. Java, node, Python, Go, etc.)
- Do you already use similar tools? (`pyenv`, `nodeenv`, etc.)
- Are you very comfortable using the shell environment? (e.g., you know what `PATH` is and how to modify it, you know what `~/.bash_profile` is and how to edit it, etc.)

Each manager has its own strengths and weaknesses. There is no _best_ manager, only the one that works best for you. That said, if you do not have any version manager installed (you are starting from scratch or are a completely new user) then I would recommend using [asdf-vm](https://asdf-vm.com/#/core-manage-asdf) as it is the most flexible and powerful. It can accommodate many languages and tools, not just Ruby, and has a large community of support. It uses the fundamentals of tools like `pyenv`, `rbenv` and `nodeenv` but is more flexible than any of them and can be used as a single tool to replace those multiple tools.

## How do I use a version manager?

The steps to install and use a version manager vary between tools and over time. Refer to the website of each manager for up-to-date instructions for installing a version manager and Ruby. Keep in mind that the version manager will download, compile, and install Ruby, but it's up to you to tell it what version you want installed (and what version you want to use in any given shell session), so make sure you carefully read the documentation for the version manager you select.

The general process for using a version manager is:

1. Download and install the manager.
2. Download and install Ruby using the manager.
3. Ensure your shell has been configured properly to use the new version of Ruby you just installed.
4. Run `which ruby` and `ruby -v` to ensure the correct version and copy of Ruby is being used.

# How do I get help?

Head over to Stack Overflow and [ask a question](https://stackoverflow.com/help/how-to-ask). There are many good people who will be happy to provide support.

Please take time to read the following articles from the [StackOverflow Help Center](https://stackoverflow.com/help) before posting a question to ensure you get the best possible help:

- [What topics can I ask about here?](https://stackoverflow.com/help/on-topic)
- [How do I ask a good question?](https://stackoverflow.com/help/how-to-ask)
- [How to create a Minimal, Reproducible Example](https://stackoverflow.com/help/minimal-reproducible-example)

# How do I update these docs?

This documentation is open source and available on [GitHub](https://github.com/anothermh/dontusesystemruby.com). Open a pull request with any recommended changes.

---

**Copyright &copy; 2023, dontusesystemruby.com**
