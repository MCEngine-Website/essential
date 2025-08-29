
# Essential AddOn Usage Guide

**Path:** `com.example.MyEssentialAddOn.java`

This document explains how to implement the `IMCEngineEssentialAddOn` interface to create a custom AddOn for the MCEngine Essential module.

## Interface

```java
package com.example;

import io.github.mcengine.api.essential.extension.addon.IMCEngineEssentialAddOn;
import io.github.mcengine.api.core.MCEngineCoreApi;
import io.github.mcengine.api.core.extension.logger.MCEngineExtensionLogger;
import org.bukkit.plugin.Plugin;

public class MyEssentialAddOn implements IMCEngineEssentialAddOn {

    /** Unique identifier for this AddOn instance. */
    private String id;

    @Override
    public void onLoad(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "AddOn", id);
        logger.info("Essential AddOn loaded with ID: " + id);
    }

    @Override
    public void onDisload(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "AddOn", id);
        logger.info("Essential AddOn unloaded with ID: " + id);
    }

    @Override
    public void setId(String id) {
        MCEngineCoreApi.setId("essential-example-api");
    }
}
```

## Description

This interface allows integration of custom AddOns into the Essential engine. It includes three main lifecycle methods for initializing and unloading your AddOn.

## Notes

- Use `onLoad` to register commands, listeners, or hooks.
- Always clean up resources in `onDisload`.
- The `id` must be unique per AddOn instance.
