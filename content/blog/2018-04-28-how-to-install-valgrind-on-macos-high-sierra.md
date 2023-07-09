---
author: Güngör Budak
date: '2018-04-28T14:00:00+03:00'
slug: how-to-install-valgrind-on-macos-high-sierra
tags:
- macos
- high sierra
- brew
- install
- valgrind
title: How to Install Valgrind on macOS High Sierra
year: '2018'
---

Valgrind is a programming tool for memory debugging, memory leak detection and profiling. Its installation for macOS High Sierra seems problematic and I wanted to write this post to tell the solution that worked for me. I use Homebrew to install it which is the recommended way and the solution also uses it.

[![Valgrind](/public/images/valgrind.png)](/public/images/valgrind.png)

So, when you try installing right away, you may get the following error:

```bash
brew install valgrind
valgrind: This formula either does not compile or function as expected on macOS
versions newer than Sierra due to an upstream incompatibility.
```

1\. To correctly install it, first, type the following command at the Terminal (which opens Valgrind's formulae)

```bash
brew edit valgrind
```

And change the URL in `head` section

```
https://sourceware.org/git/valgrind.git
```

to

```
git://sourceware.org/git/valgrind.git
```

[Solution from this post](https://github.com/Homebrew/homebrew-core/issues/23536).

2\. Do an update for Homebrew:

```bash
brew update
```

3\. Finally, use the following command to install Valgrind from the `HEAD`:

```bash
brew install --HEAD valgrind
```

[Solution from this post](https://github.com/Homebrew/homebrew-core/issues/18998).
