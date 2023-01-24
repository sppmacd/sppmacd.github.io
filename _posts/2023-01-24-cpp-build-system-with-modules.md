---
tags: ["programming"]
title: "Writing a C++ build system that supports modules"
---

Today I started creating EssaBuild, a build system for C++.

## Why a new build system?

For the same reason as everything I do. For fun. Also I was testing C++ modules and I recalled that CMake still doesn't support them. After 3 years

Don't get me wrong, I don't think CMake is "bad" or something. It's a nice tool for the thing it does, and I will continue using it until EssaBuild becomes capable enough. But there is no fun in using an existing tool when you can do it yourself!

## Goals

### Simplicity

I want API to be as simple as possible, with understandable, intuitive concepts, while maintaining flexibility. That's why build scripts are written in Python.

This is an example of "hello world" program:
```py
import essabuild as eb

# Initialize a new project.
project = eb.project("hello-world")

# Set properties that will be shared by every target.
project.compile_config.std = "c++20"
project.compile_config.defines = {"TEST_DEFINE": "TEST"}

# Add an executable
main = project.add_executable("main", sources=["main.cpp"])
```

### Performance

This basically means supporting parallel execution where possible.

### First-class code generation support

Something that I don't like in CMake is that this is so tedious to create "host tools", that is, executables that run on the host that is the build performed on, instead of the target. There are solutions in other projects:

* `npm` distinguishes between `dependencies` and `devDependencies`.
* [SerenityOS](https://github.com/SerenityOS/serenity) uses something names "superbuild" to separate its host tools from target tools.

I didn't have details planned, but I think this will be something like this:

```py

my_framework = project.add_library()

# Create a dev target.
dev_target = project.add_host_executable("generator")

# Link to target libraries - this will just work.
dev_target.link(my_framework)

# Define how the generator is run for a specified source
def generate_with_dev_target(source: eb.GeneratedSource):
    # Run a generator
    subprocess.run([dev_target.executable_path(), "-s", source.filename])

    # Return source name, relative to build dir.
    return sogeneratorurce + ".cpp"

# Add a GeneratedSource that runs generator. Generated source file is automatically linked.
my_executable.add_sources([eb.GeneratedSource("file.myformat", generate_with_dev_target)])

```

### Easy dependency handling

I want to avoid downloading manually all dependencies when building a complex project. Would it be nice to make my build system download everything:

```py
...

# Find an imported dependency or download from GitHub if not found.
other_project = eb.pull_dependency("https://github.com/essa-software/EssaGUI")

# Link dependency to target.
target.link(other_project.get_target("essa-gui"))

# Link libraries in an imported dependency to target.
target.link(other_project)

...
```

## Current progress

After a day of hacking I have a working, hacky "hello world" running:

![hello world in EssaBuild](/assets/images/essabuild_1/result.png)

I haven't uploaded source code yet. I will push the code to GitHub when I make something actually usable.

Thanks for the reading!
