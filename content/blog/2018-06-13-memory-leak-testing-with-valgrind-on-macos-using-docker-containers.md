---
author: Güngör Budak
date: '2018-06-13T10:00:00+03:00'
slug: memory-leak-testing-with-valgrind-on-macos-using-docker-containers
tags:
- valgrind
- memory leak
- memory management
- macos
- docker
title: Memory Leak Testing with Valgrind on macOS using Docker Containers
year: '2018'
---

I had some issues installing Valgrind on macOS High Sierra and [posted some tips to successfully install it to the system]({% post_url 2018-04-28-how-to-install-valgrind-on-macos-high-sierra %}). Although I could install the software this way, it didn't work correctly after testing with with several real and dummy C++ codes. It was giving me a memory leak error even with an empty code. So, then I decided to use an Ubuntu 16.04 based Docker container to test the code within the container using the Ubuntu version of Valgrind.

[![Valgrind](/public/images/valgrind.png)](/public/images/valgrind.png)

Below is a Dockerfile that will build the required Docker image. Just make a new directory called `memory-test` and `cd` into it to give Dockerfile a context and make a new file called `Dockerfile` and copy-paste below lines into it.

```
FROM ubuntu:16.04

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install g++ valgrind -y
```

Use below command to build the Docker image for the container:

```bash
docker build -t memory-test:0.1 .
```

This will generate a Docker image named `memory-test:0.1` that can be run as a container for do C++ memory testing. Any additional requirement can be added to above `Dockerfile` such as an external dependency or the container can be run interactively and such dependencies can be installed.

To do very simple memory test, I'll use following C++ code (save it as `main.cpp`).

```cpp
int main() {
    int *a = new int(5);
    // delete a;
    return 0;
}
```

This code allocates an integer in the memory and since `delete` statement is commented out, it won't delete the memory after it's done with `a`, which is a memory leak.

Finally, here is the directory structure for `memory-test`:

```bash
Gungors-MacBook-Pro:Desktop gungor$ tree memory-test/
memory-test/
├── Dockerfile
└── main.cpp
```

To actually test this code, while under the same directory:

```bash
docker run -ti -v $PWD:/test memory-test:0.1 bash -c "cd /test/; g++ -o main main.cpp && valgrind --leak-check=full ./main"
```

To break down what is what:

- `docker run -ti` is the base command and options for interactively running any Docker image
- `-v $PWD:/test` is the option for mounting current working directory (where we have the code and `Dockerfile`) under `/test/` directory within the executed container. In this way, you can keep modifying code outside the container and still test the its most up-to-date version.
- `memory-test:0.1` is the name of the Docker image that we are going to run a container from, remember we gave this name above
- `bash -c "cd /test/; g++ -o main main.cpp && valgrind --leak-check=full ./main"` is the actual command to change directory, build the C++ code and finally do memory leak check with Valgrind on the executable

So, after running this we get the following output as expected:

```
==11== Memcheck, a memory error detector
==11== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==11== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==11== Command: ./main
==11==
==11==
==11== HEAP SUMMARY:
==11==     in use at exit: 72,708 bytes in 2 blocks
==11==   total heap usage: 2 allocs, 0 frees, 72,708 bytes allocated
==11==
==11== 4 bytes in 1 blocks are definitely lost in loss record 1 of 2
==11==    at 0x4C2E0EF: operator new(unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==11==    by 0x400607: main (in /test/main)
==11==
==11== LEAK SUMMARY:
==11==    definitely lost: 4 bytes in 1 blocks
==11==    indirectly lost: 0 bytes in 0 blocks
==11==      possibly lost: 0 bytes in 0 blocks
==11==    still reachable: 72,704 bytes in 1 blocks
==11==         suppressed: 0 bytes in 0 blocks
==11== Reachable blocks (those to which a pointer was found) are not shown.
==11== To see them, rerun with: --leak-check=full --show-leak-kinds=all
==11==
==11== For counts of detected and suppressed errors, rerun with: -v
==11== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
```

It says there is 1 error, and in 1 block, there are 4 bytes definitely lost. Check out the [Valgrind's user manual](http://valgrind.org/docs/manual/quick-start.html) to read about these messages and see more examples.

To also see how it works when there is no memory leak, I put `delete a;` back and rerun the above `docker run` command. And here is the output:

```
==10== Memcheck, a memory error detector
==10== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==10== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==10== Command: ./main
==10==
==10==
==10== HEAP SUMMARY:
==10==     in use at exit: 72,704 bytes in 1 blocks
==10==   total heap usage: 2 allocs, 1 frees, 72,708 bytes allocated
==10==
==10== LEAK SUMMARY:
==10==    definitely lost: 0 bytes in 0 blocks
==10==    indirectly lost: 0 bytes in 0 blocks
==10==      possibly lost: 0 bytes in 0 blocks
==10==    still reachable: 72,704 bytes in 1 blocks
==10==         suppressed: 0 bytes in 0 blocks
==10== Reachable blocks (those to which a pointer was found) are not shown.
==10== To see them, rerun with: --leak-check=full --show-leak-kinds=all
==10==
==10== For counts of detected and suppressed errors, rerun with: -v
==10== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
```

As you see there is no error and no bytes that is definitely lost.
