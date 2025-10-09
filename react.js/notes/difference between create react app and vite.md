### **Build Speed**

- **CRA**: Slower build times, especially for large apps, because Webpack bundles everything at once.
    
- **Vite**: Uses **ESBuild** for dev and **Rollup** for production. ESBuild is extremely fast because it’s written in Go and does **on-demand, unbundled serving** in development.

### **Development Server**

- **CRA**: Hot Reloading can be slow because the entire app often needs to be rebuilt.
    
- **Vite**: Lightning-fast Hot Module Replacement (HMR). Only the module that changed is updated in the browser, so updates feel instant.

### **Configuration**

- **CRA**: Works out of the box, but **customizing Webpack** requires ejecting (`npm run eject`), which is messy.
    
- **Vite**: Config is easier, more flexible, and can be customized without “ejecting.”