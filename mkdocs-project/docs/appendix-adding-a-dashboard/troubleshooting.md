# InfoMapper / Dashboard / Troubleshooting #

This section covers major roadblocks found on the way to creating the Dashboard
and its widgets.

## mat-select usage results in "No provider for InjectionToken mat-select-scroll-strategy" ##

The selector widget uses the **mat-select** component for selecting an element from
a list. After importing the necessary modules from **@angular/material**, the following
error was displayed

```
ERROR Error: Uncaught (in promise): NullInjectorError: R3InjectorError(AppModule)[InjectionToken mat-select-scroll-strategy -> InjectionToken mat-select-scroll-strategy -> InjectionToken mat-select-scroll-strategy]: 
  NullInjectorError: No provider for InjectionToken mat-select-scroll-strategy!
```

After research, it seems that because of lazy loading, the Selector component becomes
a part of the application `AppModule`. This means that the consuming application
also needs the same imports that each module in the Common library needs. More information
on the issue can be found [here](https://github.com/angular/angular/issues/35264).

The solution, therefore, was to add the `MatSelectModule` to the InfoMapper's `AppModule`
file as an import. This resolved the issue.