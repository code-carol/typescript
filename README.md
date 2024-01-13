# TypeScript

[Documentation](https://www.typescriptlang.org/)

TypeScript is a programming language that allows us to write JavaScript with a set of tools called a type system that can spot potential bugs in, clarify the structure of, and help refactor our code.

### Summary

- [How to use it](#how-to-use-it)
- [Type Inference](#type-inference)
- [Type Shapes](#type-shapes)
- [Type Any](#type-any)
- [Type Annotations](#type-annotations)
- [The tsconfig.json File](#the-tsconfigjson-file)
- [Parameter Type Annotations](#parameter-type-annotations)
- [Optional Parameters](#optional-parameters)
- [Inferring Return Types](#inferring-return-types)
- [Explicit Return Types](#explicit-return-types)
- [Void Return Type](#void-return-type)
- [Documenting Functions](#documenting-functions)

## How to use it

### 1.

We write TypeScript code in files with the extension `.ts`.

### 2.

We run our code through the TypeScript transpiler. The transpiler will check that the code adheres to TypeScript’s standards, and it will display errors when it does not.

TypeScript transpiler can be used on the command line by running the `tsc` command.

### 3.

If the TypeScript code can be converted into working JavaScript, the transpiler will output a JavaScript version of the file (.js).

## Type Inference

When we declare a variable with an initial value, the variable can never be reassigned a value of a different data type.

```
let order = 'first';

order = 1;
```

Error: `Type 'number' is not assignable to type 'string'.`

## Type Shapes

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

## Type Any

Variables of type `any` can be assigned to any value and TypeScript won’t give an error if they’re reassigned to a different type later on.

```
let onOrOff;

onOrOff = 1;
onOrOff = false;
```

## Type Annotations

We can declare a variable and the type of the variable without an initial value.

We provide a type annotation by appending a variable with a colon `(:)` and the type (e.g., number, string, or any).

```
let mustBeAString : string;
mustBeAString = 'Catdog';

mustBeAString = 1337;
// Error: Type 'number' is not assignable to type 'string'
```

## The tsconfig.json File

The `tsconfig.json` file is always placed in the root of your project and you can customise what rules you want the TypeScript compiler to enforce.

Create the file with `tsc --init` command.

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

## Parameter Type Annotations

Function parameters can be given type annotations with the same syntax as variable declarations: a colon next to the name.

Parameters that we do not provide type annotations for are assumed to be of type any.

```
function printKeyValue(key: string, value) {
  console.log(`${key}: ${value}`);
}

printKeyValue('Courage', 1337); // Prints: Courage: 1337
printKeyValue('Mood', 'scared'); // Prints: Mood: scared
```

## Optional Parameters

To indicate that a parameter is intentionally optional, we add a `?` after its name. This tells TypeScript that the parameter is allowed to be undefined and doesn’t always have to be provided.

```
function greet(name?: string) {
  console.log(`Hello, ${name|| 'Anonymous'}!`);
}

greet(); // Prints: Hello, Anonymous!
```

## Default Parameters

If a parameter is assigned a default value, TypeScript will infer the variable type to be the same as the default value’s type.

```
function greet(name = 'Anonymous') {
  console.log(`Hello, ${name}!`);
}
```

## Inferring Return Types

TypeScript can also infer the types of values returned by functions.

```
function ouncesToCups(ounces: number) {
  return `${ounces / 16} cups`;
}

const liquidAmount: number = ouncesToCups(3);
// Type 'string' is not assignable to type 'number'.
```

## Explicit Return Types

If we’d like to be explicit about what type a function returns, we can add an explicit type annotation after its closing parenthesis.

const createArrowGreeting = (name?: string)`: string `=> {
if (name) {
return "Hello " + name!;
}

return undefined;
// Typescript Error: Type 'undefined' is not assignable to type 'string'.
};

## Void Return Type

It's often preferred to use type annotations for functions, even when those functions don’t return anything.

function logGreeting(name:string)`: void`{
console.log("Hello " + name!)
}

## Documenting Functions

It’s common in TypeScript to see a third comment style: documentation comments. A documentation comment is denoted with the first line `/**` and a final line `*/.` It’s common for each line within the comment to start with an asterisk `(*)`.

```
/**
* This is a documentation comment
*/
```

Many text editors will helpfully display documentation comments, for example, when hovering over a function name.

```
  /**
   * Returns the sum of two numbers.
   *
   * @param x - The first input number
   * @param y - The second input number
   * @returns The sum of `x` and `y`
   *
   */
  function getSum(x: number, y: number): number {
    return x + y;
  }


```
