# Theme Module Starter

You can use this template to quickly create your own theme module.  

## First steps

Update `template-values.json` with your theme name, machine name, and the theme module version, and the `hook_module_info` hook (`public/views/partials/lib/hooks/hook_module_info.liquid`) with any additional dependencies.  
We strongly recommend the use of the [Theme Manager Module](https://github.com/Platform-OS/pos-module-theme-manager):
```
  "dependencies": [
    "core",
    "theme-manager"
  ]
```

Update the `hook_theme_variables` hook (`public/views/partials/lib/hooks/hook_theme_variables.liquid`) with your default color scheme, theme related css/js assets, and any other design tokens and theme variables.  

You can provide your own theme-specific components and/or component overrides in `public/views/partials/components`.  
Check the official documentation of the [Component Library Module](https://github.com/Platform-OS/pos-module-components#usage) for more details on how component overrides work. 

## What is a theme?

A theme is a combination of **configuration** (colors and other design tokens), **static assets** (images, css/js files), and **components, layouts and page templates** (home page template, header component, or component overrides for an existing component).  
Try to avoid adding any business logic: your theme should focus on the UI and the presentational layer.

## Working with other modules

### Theme manager & Admin module

The [Theme Manager Module](https://github.com/Platform-OS/pos-module-theme-manager) will find your theme automatically based on your `hook_module_info` implementation using the [Core Module](https://github.com/Platform-OS/pos-module-core)'s module registry.  
If you have the Theme manager and the [Admin Module](https://github.com/Platform-OS/pos-module-admin) enabled then you'll be able to select your custom theme as the default one and see the color scheme editor and the live preview on the admin UI.

The theme manager will automatically show a live preview for the theme if you implement one.  
You can provide it in the `hook_module_info` hook's payload (`preview` property). The value should be the relative path to the liquid partial file you want to be rendered on the Admin UI.  
This starter implements a simple static HTML preview. If you want to use the standard components from the Component Library module then it's recommended to build your preview template from the existing components.

You can create your custom admin layout for the Admin Module by implementing the `hook_theme_admin_layout` hook: see the relevant section of the [Theme Manager documentation](https://github.com/Platform-OS/pos-module-theme-manager#hooks).

### Component Library
You can use the standard atomic components from the [Component Library Module](https://github.com/Platform-OS/pos-module-components) and provide theme-level component overrides in your theme.  
To use this feature, set up the `theme_search_path` in your app config file and use the naming convention for your theme components: Your components should follow the original components' folder structure and filename.  

It's important to keep your component overrides backwards compatible with the original components in the Component Library. This is how you ensure that existing high-level components (molecules, organisms) that use the original components will still work as expected with your new component overrides.  

Example:  
If you create a new Icon component for your theme to add a custom iconset, you should implement the same component parameters because that's how other existing components expect the Icon component to work. If your custom Icon component is backwards compatible with the default one from the Component Library then other higher-level components (e.g. the Icon Button, or the Alert component) can automatically use the new version of the Icon component without any side-effects or unexpected results.


# Theme documentation  

You can provide your own documentation here.  

Some examples: theme screenshot, color scheme, a list of components and component overrides, hook implementations, etc
