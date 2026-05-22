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

# Setup

`//TODO: maven repo`

# Config Structure

All you need to do to get started is to make a class and annotate it with `@GooberConfig(modId = "testmod")`

For those of you who dearly miss your beloved builderslop, we have that! 

```java
@GooberConfig(modId = "testmod")
public class TestConfig {
  public static final IntOption int1 = new IntOption("Standalone field", "meow");

  // GooberLib looks for a field of type GooberConfigBuilder
  public static final GooberConfigBuilder BUILDER = GooberConfigBuilder
            // overloads for passing either a String or a Text object
            .create("YEAH!!!")
              .category("Int fields", "A description")
                .options(int1)
                .build();
}
```

For those of you who don't, we've heavily condensed the process to allow more time for writing real code instead of config code.

```java

@GooberConfig(modId = "testmod")
public class TestConfig {
  public static final IntOption int1 = new IntOption("Standalone field", "meow");
  public static final GooberConfigBuilder BUILDER = GooberConfigBuilder.create("YEAH!!!", config -> {
	  config.category("Int fields", "A description", category -> {
			category.options(int1);
			// No .build()!
		});
	});
}
	
```

Alternatively, use MAGIC (Multi-Annotation GooberLib-Inferred Configuration):

```java
@GooberConfig(modId = "testmod")
public class TestConfig {

  // If a GooberConfigBuilder field is not found, MAGIC will be used instead.
  // TODO:
  public static final IntOption int1 = new IntOption("Standalone field", "meow");

}
```