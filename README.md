# Repo for reproduction

This is an NX workspace with Angular preset, plus Jest. It adds the Clarity Design System and uses one of its modules in
a Jest test. The test however does not complete anymore.

## Steps to reproduce this repository

Create an Nx workspace with

```
npx create-nx-workspace@latest
```

and select "Angular" as preset. Then install the clarity dependencies as follow:

```
npm i @cds/{core,angular} --legacy-peer-deps
```

Then add one of the Clarity modules to the TestBed configuration of the unit test like here:

https://github.com/ngfelixl/clarity-jest-test/blob/f77718a8c5358f32cb1fba98edc1581ddd0c6122/apps/app/src/app/app.component.spec.ts#L9


## Run the tests

```
npx nx run-many --target=test --all
```

## Error message

```
Jest encountered an unexpected token

Jest failed to parse a file. This happens e.g. when your code or its dependencies use non-standard JavaScript syntax, or when Jest is not configured to support such syntax.

Out of the box Jest supports Babel, which will be used to transform your files into valid JS based on your Babel configuration.

By default "node_modules" folder is ignored by transformers.

Here's what you can do:
 • If you are trying to use ECMAScript Modules, see https://jestjs.io/docs/ecmascript-modules for how to enable it.
 • If you are trying to use TypeScript, see https://jestjs.io/docs/getting-started#using-typescript
 • To have some of your "node_modules" files transformed, you can specify a custom "transformIgnorePatterns" in your config.
 • If you need a custom transformation specify a "transform" option in your config.
 • If you simply want to mock your non-JS modules (e.g. binary assets) you can stub them out with the "moduleNameMapper" config option.

You'll find more details and examples of these config options in the docs:
https://jestjs.io/docs/configuration
For information about custom transformations, see:
https://jestjs.io/docs/code-transformation

/PATHTO/clarity-jest-test/node_modules/@cds/core/accordion/register.js:1
({"Object.<anonymous>":function(module,exports,require,__dirname,__filename,jest){import{registerElementSafely as o,ClarityMotion as r,AnimationAccordionPanelOpenName as c,AnimationAccordionPanelOpenConfig as e}from"@cds/core/internal";import{CdsAccordion as n}from"./accordion.element.js";import{CdsAccordionPanel as d}from"./accordion-panel.element.js";import{CdsAccordionContent as t}from"./accordion-content.element.js";import{CdsAccordionHeader as i}from"./accordion-header.element.js";import"@cds/core/icon/register.js";import"@cds/core/button-expand/register.js";o("cds-accordion",n),o("cds-accordion-panel",d),o("cds-accordion-content",t),o("cds-accordion-header",i),r.add(c,e);
                                                                                  ^^^^^^


SyntaxError: Cannot use import statement outside a module

  at Runtime.createScriptFromCode (../../node_modules/jest-runtime/build/index.js:1796:14)
```
