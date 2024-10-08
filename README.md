# AutoPkg Recipes Repository

Welcome to Vaxa's `autopkg-recipes` repository. This repository contains our custom AutoPkg recipes for automating software packaging, deployment, and management workflows in our MacOS environments. 

The goal is to provide a consistent and reliable way to maintain software across our environments, and meet our security and compliance requirements around timely software updates.

## 📂 Folder Structure

- **`recipes/`**  
  Contains custom recipes developed specifically for our environment. Each application has its own subdirectory to logically group `.download`, `.pkg`, `.munki`, or other recipe types.
  
- **`overrides/`**  
  Holds override recipes that customise public recipes with specific settings for our organisation. This is used when we need to modify existing community recipes with minor changes (e.g., custom package names or post-processing steps). Usually, we'll opt for `/overrides` in our `autopkg` repository rather than here, though.

- **`SharedProcessors/`**  
  Includes any custom processors that extend AutoPkg’s functionality. These can be used to perform unique tasks required by our workflows that are not covered by default AutoPkg processors.

## 🗂️ Recipe Organisation

Each application is organised into its own folder under the `recipes/` directory. For example:

```
autopkg-recipes/
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
2. **Create a new directory** in the `recipes/` folder with the name of the application.
2. Add the relevant recipe files (`.download`, `.pkg`, `.munki`, etc.) following AutoPkg’s XML format.
3. **Test the recipe** locally:
   ```bash
   autopkg run -v path/to/recipe.recipe
4. **Commit the changes** and submit a pull request to this repository to merge your changes into the `main` branch.