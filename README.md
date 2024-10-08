# AutoPkg Recipes Repository

Welcome to Vaxa's `autopkg-recipes` repository. This repository contains our custom AutoPkg recipes for automating software packaging, deployment, and management workflows in our MacOS environments. 

The goal is to provide a consistent and reliable way to maintain software across our environments, and meet our security and compliance requirements around timely software updates.

This repository is referenced by our [AutoPkg setup](https://github.com/vaxa-tech/autopkg), which is in turn used to populate our [Munki environment](https://github.com/vaxa-tech/munki). 

## 🗂️ Recipe Organisation

Each application is organised into its own folder under the repo's root directory. For example:

```
vaxa-tech/autopkg-recipes/
├── VLC/ 
│ ├── VLC.download.recipe 
│ ├── VLC.pkg.recipe 
│ └── VLC.munki.recipe
├── Firefox/ 
│ ├── Firefox.download.recipe 
│ ├── Firefox.pkg.recipe 
│ └── Firefox.munki.recipe 
├── MyCustomProcessor/ 
│ ├── README.md 
│ ├── MyCustomProcessor.recipe 
│ └── MyCustomProcessor.py
```

### Recipe Types:

- **`.download.recipe`:** Defines how to download the application.  
- **`.pkg.recipe`:** Creates a macOS installer package (`.pkg`) from the downloaded application.  
- **`.munki.recipe`:** Prepares the package for deployment through Munki.  
- **`.py`:** Custom processor recipes that extend AutoPkg’s functionality.

## ➕ Adding a New Recipe

1. **Create yourself a new branch** in this repo.
2. **Create a new directory** in the root folder with the name of the application e.g. `MyApp/`.
3. Add the relevant recipe files (`.download`, `.pkg`, `.munki`, etc.) following AutoPkg’s XML format.
4. `cd` into your `MyApp/` directory so you can test.
5. **Test each recipe** locally:
   ```bash
   autopkg run -vv MyApp.download.recipe
   # you may need to ignore trust issues during testing, but these must be resolved before merging
   autopkg run -vv --ignore-parent-trust-verification-errors MyApp.download.recipe
   ```
6. **Commit the changes** and submit a pull request to this repository to merge your changes into the `main` branch.