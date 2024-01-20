# 🎯 Functions

<details>
   <summary>
     <h2>⭐️ Parameter Type Annotations</h2>
   </summary>

Function parameters can be given type annotations with the same syntax as variable declarations: a colon next to the name.

Parameters that we do not provide type annotations for are assumed to be of type any.

```
function printKeyValue(key: string, value) {
  console.log(`${key}: ${value}`);
}

printKeyValue('Courage', 1337); // Prints: Courage: 1337
printKeyValue('Mood', 'scared'); // Prints: Mood: scared
```

</details>

<details>
   <summary>
     <h2>⭐️ Optional Parameters</h2>
   </summary>

To indicate that a parameter is intentionally optional, we add a `?` after its name. This tells TypeScript that the parameter is allowed to be undefined and doesn’t always have to be provided.

```
function greet(name?: string) {
  console.log(`Hello, ${name|| 'Anonymous'}!`);
}

greet(); // Prints: Hello, Anonymous!
```

</details>

<details>
   <summary>
     <h2>⭐️ Default Parameters</h2>
   </summary>

If a parameter is assigned a default value, TypeScript will infer the variable type to be the same as the default value’s type.

```
function greet(name = 'Anonymous') {
  console.log(`Hello, ${name}!`);
}
```

</details>

<details>
   <summary>
     <h2>⭐️ Inferring Return Types</h2>
   </summary>

TypeScript can also infer the types of values returned by functions.

```
function ouncesToCups(ounces: number) {
  return `${ounces / 16} cups`;
}

const liquidAmount: number = ouncesToCups(3);
// Type 'string' is not assignable to type 'number'.
```

</details>

<details>
   <summary>
     <h2>⭐️ Explicit Return Types</h2>
   </summary>

If we’d like to be explicit about what type a function returns, we can add an explicit type annotation after its closing parenthesis.

const createArrowGreeting = (name?: string)`: string `=> {
if (name) {
return "Hello " + name!;
}

return undefined;
// Typescript Error: Type 'undefined' is not assignable to type 'string'.
};

</details>

<details>
   <summary>
     <h2>⭐️ Void Return Type</h2>
   </summary>

It's often preferred to use type annotations for functions, even when those functions don’t return anything.

function logGreeting(name:string)`: void`{
console.log("Hello " + name!)
}

</details>

<details>
   <summary>
     <h2>⭐️ Documenting Functions</h2>
   </summary>

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

</details>
