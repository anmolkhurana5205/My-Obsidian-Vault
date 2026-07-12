It is tool that comes with NPM.
It is used to run packages without installing them globally.
### 🔥 The Actual Thing:

When you run a package with `npx`, if you **don’t already have it installed anywhere**, `npx` will:

1. **Download it temporarily** from the npm registry.
    
2. **Run it directly from that temporary location** (not your project’s `node_modules`, not global).
    
3. **Delete it after running** (or cache it internally).
    

So it’s not really “global” or “local” in your project — it’s just **temporary** for that command.