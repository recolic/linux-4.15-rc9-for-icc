## Latest Linux Kernel by Intel C++ Compiler

I made some attempts to compile latest linux kernel with Intel C++ Compiler, and what I've done is recorded here.

Kernel version here is 4.15.0-rc9. You can just rebase my commits to your preferred version. (Be causion before rebasing!)

It succeeded to run in my ubuntu 16.04 virtual machine, with some error messages printed to journal. But mostly speaking, it works pretty good.

### How to compile

```sh
git clone ... && cd ...
cp icc-wrapper /usr/bin/icc-wrapper
# Make sure that icc is in your $PATH, or you can edit icc-wrapper to help it to find icc.
make xconfig/menuconfig/...
make CC=icc-wrapper HOSTCC=icc-wrapper
sudo make install
sudo reboot
```

### What have I done

- Edited some kernel source code to fit icc. Review them please.

- Edit Makefile: change all -O2 to -O3. Cancel it if you prefer.

- Write icc-wrapper.

### What have I gotten

![Img: nginx server on icc-compiled kernel](https://recolic.net/tmp/snap-0202-221446.png)



origin README by kernel developers
---------------------------------

Linux kernel
============

This file was moved to Documentation/admin-guide/README.rst

Please notice that there are several guides for kernel developers and users.
These guides can be rendered in a number of formats, like HTML and PDF.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.
See Documentation/00-INDEX for a list of what is contained in each file.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.
