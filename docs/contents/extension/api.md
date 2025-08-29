
# Essential API Module Usage Guide

**Path:** `com.example.MyEssentialAPI.java`

This document explains how to implement the `IMCEngineEssentialAPI` interface to create a central API module for the MCEngine Essential system.

## Interface

```java
package com.example;

import io.github.mcengine.api.essential.extension.api.IMCEngineEssentialAPI;
import io.github.mcengine.api.core.MCEngineCoreApi;
import io.github.mcengine.api.core.extension.logger.MCEngineExtensionLogger;
import org.bukkit.plugin.Plugin;

public class MyEssentialAPI implements IMCEngineEssentialAPI {

    /** Unique identifier for this API module. */
    private String id;

    @Override
    public void onLoad(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "API", id);
        logger.info("Essential API loaded with ID: " + id);
    }

    @Override
    public void onDisload(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "API", id);
        logger.info("Essential API unloaded with ID: " + id);
    }

    @Override
    public void setId(String id) {
        MCEngineCoreApi.setId("artificialintelligence-example-api");
    }
}
```

## Description

This interface serves as the core API layer for Essential systems. It should manage shared features, provide utilities, and expose cross-module integrations.

## Notes

- Ideal for backend processing and shared logic.
- Avoid direct player events in the API; delegate to AddOns or DLCs.
