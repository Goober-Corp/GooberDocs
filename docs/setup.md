---
title: Getting Started
date: 2026-05-21
description: Setting up GooberLib
authors:
  - kr1v
  - tektonikal
draft: false
comments: false
---

`//TODO: maven repo`

# Config Structure

All you need to do to get started is to make a class and annotate it with `@GooberConfig(modId = "testmod")`

For those of you who dearly miss your beloved builderslop, we have that!

```java
public static final IntOption int1 = new IntOption("Standalone field", "meow");

public static final GooberConfigBuilder BUILDER = GooberConfigBuilder
          //overloads for passing either a String or a Text object
          .create("YEAH!!!")
            .category("Int fields", "A description")
              .option(int1)
              .build()
            .build();
```
