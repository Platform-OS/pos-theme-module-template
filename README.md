# Theme Module Starter

You can use this template to quickly create your own theme module.  

# First steps

Update the `hook_module_info` hook (`public/views/partials/lib/hooks/hook_module_info.liquid`) with your theme name, machine name and additional dependencies.  
We strongly recommend the use of the [Theme Manager Module](https://github.com/Platform-OS/pos-module-theme-manager):
```
  "dependencies": [
    "core",
    "theme-manager"
  ]
```

Update the `hook_theme_variables` hook (`public/views/partials/lib/hooks/hook_theme_variables.liquid`) with your theme's machine name ("theme" property) and your theme variables.  

You can provide your own theme-specific components and/or component overrides in `public/views/partials/components`.  
For more details about how component overrides work you can check the official documentation of the [Component Library Module](https://github.com/Platform-OS/pos-module-components#usage).

# Theme documentation  

You can provide your own documentation here.  

Some examples: theme screenshot, color scheme, a list of components and component overrides, hook implementations, etc