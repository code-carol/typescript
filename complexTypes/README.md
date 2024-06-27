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
