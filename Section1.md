## What is the difference between C# and .NET

. C# is a programming language

. .NET is a framework for building applications on Windows

.NET framework is not limited to C#, there are different languages that can target .NET framework and build applications
using that same framework, like F# and VB.NET.

It consist of two components: CLR and the other is a class library for building applications

## CLR (Common Language Runtime)

First, let's take a look on C# history

Before C#, we had two languages in the C family, the C and C##. With either of these languages, when we compiled our app,
the compiler translated our code into the native code for the machine in which it was running. Which means if i wrote
an app in C## in a windows machine, with 80 86 processor architecture. The compiler would translate our code into the
native code for that machine.

Nowadays we have different hardwares. And different OSs. So if we took an application that compiled the application on
the computer with a different architecture, that would not run. So when Microsoft was designing C-Sharp language on the
.NET framework they came up with an idea that they borrowed from the Java community.

in Java, the compiled code is not translated directly into machine code. It is translated into an intermediate language
called bytecode and we have the exact same concept in C-sharp. When we compile our C# code. The result is what we call
IL or intermediate language code, it is independent of the computer in which it is running. Now we need something that
would translate that code into the native code of the machine that is the running the application, and that is the job
of CLR (Common Language Runtime).

CLR is essentially an application that is sitting in the memory whose job is to translate the code into the machine
code. And this process is called just in time compilation or JIT.

With this architecture, as long as the machine has CLR, it can run our application

## Architecture of .NET applications

At a very high level when we build an application with C#, our application consists of building blocks called classes,
these classes collaborate with each other in runtime and as a result, the application provides some functionality.

A Class is basically a container that has some data which is also called attributes and functions - which is also called
methods.

Functions or methods have behavior. They execute code and data represent the state of the application. 

As the number of classes in an application grows, we need a way to organize these classes. That's where we use a namespace.

A namespace is a container for related classes. For example, in .NET framework we have namespaces, each containing tens
of related classes. We have namespaces for working with data, like databases, we also have namespaces for working with
graphics/images, other for security, etc.

In real world application as these namespaces grow, we need a way for partitioning an application and that's where we use
an assembly. An assembly is a container for related namespaces.

Physically it is a file on the disk which can either be an executable or a DLL, which stands for dynamically linked library.

When we compile an application, the compiler builds one or more assemblies depending on how we partition our code.