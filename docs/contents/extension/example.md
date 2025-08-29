
# AI API Module Usage Guide

**Path:** `com.example.MyAIAPI.java`
[`Example Repository`](https://github.com/MCEngine-Extension/artificialintelligence-api-example)

This document explains how to implement the `IMCEngineArtificialIntelligenceAPI` interface to create a core AI API module for the MCEngine.

## Interface

```java
package com.example;

import io.github.mcengine.api.artificialintelligence.extension.api.IMCEngineArtificialIntelligenceAPI;
import io.github.mcengine.api.core.MCEngineCoreApi;
import io.github.mcengine.api.core.extension.logger.MCEngineExtensionLogger;
import org.bukkit.plugin.Plugin;

public class MyAIAPI implements IMCEngineArtificialIntelligenceAPI {

    /** Unique identifier for this AI API module. */
    private String id;

    @Override
    public void onLoad(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "API", id);
        logger.info("AI API loaded with ID: " + id);
    }

    @Override
    public void onDisload(Plugin plugin) {
        MCEngineExtensionLogger logger = new MCEngineExtensionLogger(plugin, "API", id);
        logger.info("AI API unloaded with ID: " + id);
    }

    @Override
    public void setId(String id) {
        MCEngineCoreApi.setId("essential-example-api");
    }
}
```

## Description

This interface provides core AI functionality for the MCEngine. It should be used for backend logic and foundational services.

## Notes

- Best for systems that power other modules.
- Avoid player-specific logic; use backend-oriented patterns.
