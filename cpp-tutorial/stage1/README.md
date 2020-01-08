Modified WORKSPACE:

```
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "rules_cc",
    sha256 = "e75dfb05bc1e89ebbb6696cadb5e455833690009310d9dc5512151c5adb0e4e3",
    strip_prefix = "rules_cc-cfe68f6bc79dea602f2f6a767797f94a5904997f",
    urls = [         
  "https://github.com/bazelbuild/rules_cc/archive/cfe68f6bc79dea602f2f6a767797f94a5904997f.zip",
    ],
)
```
---
# Stage 1

This showcases how to build a single file to create a runnable application.

This BUILD file shows that we want to build a C++ binary using the ```cc_binary``` rule provided by Bazel.
In the ```cc_binary``` rule, name of the binary is specified in ```name``` attribute (in this example, it's ```hello-world```), required source files to be built are provided in ```srcs``` attribute.

```
cc_binary(
    name = "hello-world",
    srcs = ["hello-world.cc"],
)
```

To build this example you use (notice that 3 slashes are required in windows)
```
bazel build //main:hello-world

# In Windows, note the three slashes

bazel build ///main:hello-world
```

If the build is successful, Bazel prints the following output:
```
____Loading complete.  Analyzing...
____Found 1 target...
____Building...
Target //main:hello-world up-to-date:
  C:/tools/msys64/tmp/_bazel_woden/vqeu6v3v/execroot/__main__/bazel-out/msvc_x64-fastbuild/bin/main/hello-world.exe
____Elapsed time: 0,400s, Critical Path: 0,01s
```

In the run log above you can see where the executable was built so you can locate it and use it.
