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
an app in C# in a windows machine, with 80 86 processor architecture. The compiler would translate our code into the
native code for that machine.

Nowadays we have different hardwares. And different OSs. So if we took an application that compiled the application on
the computer with a different architecture, that would not run. So when Microsoft was designing C-Sharp language on the
.NET framework they came up with an idea that they borrowed from the Java community.

in Java, the compiled code is not translated directly into machine code. It is translated into an intermediate language
called bytecode and we have the exact same concept in C-sharp. When we compile our C# code, the result is what we call
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

## First Visual Studio Application

Click on File -> New Project and on the dialog, choose Console Application

A console application is a very simple application that does not have a GUI. 

## Solution Concept

In VS we have the concept of solution where we can have one or more projects. As the application grows we have more than
one project where each is is responsible for something different.

Even though Visual Studio has many menus, panels, and may look confusing, 90% of the time we only use 10% of that and
maybe even less. Mostly using the code editor and sometimes the solution explorer (Even though that through the keyboard
many shortcuts can even be enough).

## Namespace & Assembly

### What is an assembly?

An assembly is, in short, a .NET compiled code.

Normally it is .dll and .exe

For example, when we compile our `HelloWorld` project, C# transforms our code into something like

`HelloWorld.dll`

This file is an assembly.

In the same way, .NET itself provides out-of-the-box assemblies with functionalities we may use

In legacy .NET Framework, inside references, we probably see things like

. System
. System.Core
. System.Data
...

These are references for the assemblies provided by .NET Framework.

For instance, the assembly System.dll contains multiple functionalities that the program may use.

The idea is something like

Our program -> references System.dll -> uses functionalities it has

### Solution Explorer / Instructor's Project Differences / Modern Approach

We created a console application, and on the side we can see the solution explorer (in case we don't see that, simply click
on "Exibir" and "Gerenciador de Soluções")

At the top of the Solutions Manager we will see that we have a `HelloWorld` solution, and it has only one project, HelloWorld.

#### Difference 1 - Assembly Info

My project is a little bit different from the instructor's one. Mine is more modern.

His project was created with a file named `AssemblyInfo`, which used to hold information like

```cs
[assembly: AssemblyTitle("HelloWorld")]
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyCopyright(...)]
```

But nowadays they are kept inside the file of the project, like `HelloWorld.csproj`

VS/SDK generates the AssemblyCode automatically during compiling.

If we right click on our "HelloWorld" project and then "Edit Project File", we will see something like

```cs
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net11.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

Meaning that it is not lacking an AssemblyInfo, the compiling form simply changed.

#### Difference 2 - App.config

App.config was very common on .NET Framework projects. But now a modern console app doesn't create App.config by default,
because this configuration system preferably belongs to .NET Framework old model.


#### Back to example

Under "Dependencias", we can see everything .NET is using to run this project. When we create a project with Visual Studio,
by default it has a reference to a bunch of Assemblies that we see here, which are all part of .NET framework. So at a minimum
Visual Studio assume we're going to use classes in system assembly or system that 
