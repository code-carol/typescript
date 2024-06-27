# 💻 TypeScript

[Documentation](https://www.typescriptlang.org/)

TypeScript is a programming language that allows us to write JavaScript with a set of tools called a type system that can spot potential bugs in, clarify the structure of, and help refactor our code.

## ⭐️ How to use it

### 1.

We write TypeScript code in files with the extension `.ts`.

### 2.

We run our code through the TypeScript transpiler. The transpiler will check that the code adheres to TypeScript’s standards, and it will display errors when it does not.

TypeScript transpiler can be used on the command line by running the `tsc` command.

Makes the transpiled code slightly smaller, when transpiling large programs, the file size savings can be significant `tsc fileName.ts --target esnext`.

### 3.

If the TypeScript code can be converted into working JavaScript, the transpiler will output a JavaScript version of the file (.js).

## ⭐️ The tsconfig.json File

The `tsconfig.json` file is always placed in the root of your project and you can customise what rules you want the TypeScript compiler to enforce.

- Create the file with `tsc --init` command.
- Default config `npm run tsc -- --init` command.
- Once TypeScript is running in watch mode, the type-checking output will automatically update as we save changes to TypeScript files. `npm run tsc -- --watch`

```
{
  "compilerOptions": {
    "target": "es2017",
    "module": "commonjs",
    "strictNullChecks": true,
    "outDir": "./build",
    "noUnusedLocals": true
  },
  "include": ["**/*.ts"]
}
```

In the JSON, there are several properties:

- "compilerOptions", which is a nested object that contains the rules for the TypeScript compiler to enforce.

- "target", the value "es2017" means the project will be using the 2017 version of EcmaScript standards for JavaScript.

- "module", this project will be using "commonjs" syntax to import and export modules.

- "strictNullChecks", variables can only have null or undefined values if they are explicitly assigned those values.

- "include" that determines what files the compiler applies the rules to. In this case ["**/*.ts"] means the compiler should check every single file that has a .ts extension.

- "outDir" add the js files to a folder in your directory

- "noUnusedLocals" shows all the variables that are not being used

### Configuration reference

[TS Config Options](https://www.typescriptlang.org/tsconfig/#compilerOptions)

- compilerOptions: The bulk of options. Covers how TypeScript should type check and transpile code into JavaScript.
- exclude: Specifies an array of globs (like src/\*_/_) to remove from files defined in include.
- extends: Loads an external TypeScript configuration file as the base configuration. This makes sharing common configurations possible.
- files: Specifies specific files to include.
- include: Specifies an array of globs (like src/\*_/_) to include.

### Common Configuration Properties

- strict: When true, requires that all code must adhere to a variety of type standards, like passing proper arguments to methods and treating null and undefined as separate types. Often projects will enable strict, but then override specific parts of strict by turning off features like the strictFunctionTypes option.

- paths: Allows re-mapping imports. If we have imports like import MyComponent from './app/src/components/MyComponent', we may want to shorten the import path to a shorthand path like '~/components/MyComponent'. The paths option allows us to define convenient short-hand conventions for paths when writing code. When TypeScript transpiles our code, it will use this mapping to insert the correct paths.

- allowJS: The allowJs compiler option allows constructs declared in JavaScript files to factor into type-checking TypeScript files. This is a great option to set to true when migrating a JavaScript codebase to TypeScript.

- noUnusedParameters: Ensures that every parameter defined on a function is used inside the function.

- noUnusedLocals: Ensures that every defined variable is used somewhere.

- sourceMap: Generates source map files, which help debuggers and error reporting services display the original TypeScript code when reporting errors, instead of the transpiled and minified JavaScript code.

- resolveJsonModule: Allows importing \*.json files inside TypeScript files.

## ⭐️ Type Inference

When we declare a variable with an initial value, the variable can never be reassigned a value of a different data type.

```
let order = 'first';

order = 1;
```

Error: `Type 'number' is not assignable to type 'string'.`

## ⭐️ Type Shapes

TypeScript knows what types our objects are, it also knows what shapes our objects adhere to. An object’s shape describes, among other things, what properties and methods it does or doesn’t contain.

```
"OH".length; // 2
"MY".toLowerCase(); // "my"
```

```
"MY".toLowercase();
// Property 'toLowercase' does not exist on type '"MY"'.
// Did you mean 'toLowerCase'?
```

## ⭐️ Type Any

Variables of type `any` can be assigned to any value and TypeScript won’t give an error if they’re reassigned to a different type later on.

```
let onOrOff;

onOrOff = 1;
onOrOff = false;
```

## ⭐️ Type Annotation

We can declare a variable and the type of the variable without an initial value.

We provide a type annotation by appending a variable with a colon `(:)` and the type (e.g., number, string, or any).

```
let mustBeAString : string;
mustBeAString = 'Catdog';

mustBeAString = 1337;
// Error: Type 'number' is not assignable to type 'string'
```
