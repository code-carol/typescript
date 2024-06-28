# 🌿 Complex Types

## ⭐️ Array Type Annotations

Add `[]` after the element type.

```
let names: string[] = ['Danny', 'Samantha'];
```

An alternative method is to use the `Array<T>` syntax, where `T` stands for the type.

```
let names: Array<string> = ['Danny', 'Samantha'];
```

## ⭐️ Multi-dimensional Arrays

Arrays of arrays (of some type). Add `[][]` (string[])[] to declare an array type

```
let arr: string[][] = [['str1', 'str2'], ['more', 'strings']];
```

## ⭐️ Class types

TypeScript uses keywords to control properties and methods that are used in classes.

- public: Primarily useful for readability reasons, since all properties and methods are public in JavaScript.

- private: Prevents all derived classes and instances from accessing properties and methods.

- protected: Only allows derived classes to access properties and methods, and prevents all class instances from accessing.

- readonly: Prevents reassigning a property or method, except in the class’ .constructor() method.
