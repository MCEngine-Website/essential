# Configuration

**Essential Home** does not require a dedicated config file — simply drop the JAR into:

**`plugins/MCEngineEssential/extensions/addons/`**

It will automatically create its database schema on first run.

```
# Configuration file for Essential Home AddOn

license: free
```

**Database Selection**
The database backend is chosen from the main Essential config (`plugins/MCEngineEssential/config.yml`):

```yaml
database:
  type: sqlite # or mysql, postgresql
```
