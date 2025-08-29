
# Essential Library Module Usage Guide

**Path:** `com.example.MyEssentialLibrary.java`

This document explains how to implement the `IMCEngineEssentialLibrary` interface to build a supporting library for Essential features.

## Interface

```java
package com.example;

import io.github.mcengine.api.essential.extension.library.IMCEngineEssentialLibrary;
import io.github.mcengine.api.core.MCEngineCoreApi;
import io.github.mcengine.api.core.extension.logger.MCEngineExtensionLogger;
import org.bukkit.plugin.Plugin;

public class MyEssentialLibrary implements IMCEngineEssentialLibrary {

    /** Unique identifier for this Library module. */
    private String id;

    @Override
    public void onLoad(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "Library", id);
        logger.info("Essential Library loaded with ID: " + id);
    }

    @Override
    public void onDisload(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "Library", id);
        logger.info("Essential Library unloaded with ID: " + id);
    }

    @Override
    public void setId(String id) {
        MCEngineCoreApi.setId("artificialintelligence-example-api");
    }
}
```

## Description

This interface is used to build shared libraries or backend utilities that support Essential systems. Ideal for logic reused across AddOns or APIs.

## Notes

- Should not manage any plugin-specific lifecycle beyond its utility role.
- Can provide helper classes or services for other modules.
