
# Essential DLC Module Usage Guide

**Path:** `com.example.MyEssentialDLC.java`
[`Example Repository`](https://github.com/MCEngine-Extension/essential-dlc-example)

This document explains how to implement the `IMCEngineEssentialDLC` interface to create an Essential DLC for the MCEngine.

## Interface

```java
package com.example;

import io.github.mcengine.api.essential.extension.dlc.IMCEngineEssentialDLC;
import io.github.mcengine.api.core.MCEngineCoreApi;
import io.github.mcengine.api.core.extension.logger.MCEngineExtensionLogger;
import org.bukkit.plugin.Plugin;

public class MyEssentialDLC implements IMCEngineEssentialDLC {

    /** Unique identifier for this DLC module. */
    private String id;

    @Override
    public void onLoad(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "DLC", id);
        logger.info("Essential DLC loaded with ID: " + id);
    }

    @Override
    public void onDisload(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "DLC", id);
        logger.info("Essential DLC unloaded with ID: " + id);
    }

    @Override
    public void setId(String id) {
        MCEngineCoreApi.setId("essential-example-api");
    }
}
```

## Description

This interface enables modular content packs that leverage or enhance Essential systems.

## Notes

- Use `onLoad` to add new features or integrations.
- Ensure proper cleanup in `onDisload` to prevent dangling hooks.
