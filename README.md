# Typescript-basics
### TypeScript Guide

Welcome to the basic guide to TypeScript. This guide provides an overview of TypeScript, its installation, key features, and various ways it can be used. This guide is tailored for your markdown GitHub repository.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Installing TypeScript](#installing-typescript)
3. [Basic Types](#basic-types)
4. [Interfaces](#interfaces)
5. [Classes](#classes)
6. [Functions](#functions)
7. [Modules](#modules)
8. [Generics](#generics)
9. [Type Inference](#type-inference)
10. [Advanced Types](#advanced-types)
11. [Decorators](#decorators)
12. [Conclusion](#conclusion)

---

## Introduction

TypeScript is a strongly typed superset of JavaScript that compiles to plain JavaScript. Developed and maintained by Microsoft, TypeScript enhances JavaScript by adding static types, classes, and interfaces, making it suitable for large-scale applications. 

---

## Installing TypeScript

There are two primary ways to install TypeScript:

1. **Using npm (Node Package Manager)**
    ```bash
    npm install -g typescript
    ```
    After installation, you can check the version of TypeScript using:
    ```bash
    tsc --version
    ```

2. **Using Visual Studio Plugins**
    - For Windows users, installing the Visual Studio TypeScript plugin can be more convenient.
    - Ensure you have Visual Studio installed, then download and install the necessary TypeScript plugin.

---

## Basic Types

TypeScript supports various data types to ensure type safety:

- **Boolean**
    ```typescript
    let isDone: boolean = false;
    ```

- **Number**
    ```typescript
    let decimal: number = 6;
    ```

- **String**
    ```typescript
    let color: string = "blue";
    ```

- **Array**
    ```typescript
    let list: number[] = [1, 2, 3];
    ```

- **Tuple**
    ```typescript
    let x: [string, number];
    x = ["hello", 10]; // OK
    ```

- **Enum**
    ```typescript
    enum Color {Red, Green, Blue}
    let c: Color = Color.Green;
    ```

- **Any**
    ```typescript
    let notSure: any = 4;
    notSure = "maybe a string instead";
    ```

- **Void**
    ```typescript
    function warnUser(): void {
        console.log("This is a warning message");
    }
    ```

---

## Interfaces

Interfaces define the structure of an object, ensuring proper type-checking.

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

function greet(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = { firstName: "John", lastName: "Doe" };
console.log(greet(user));
```

---

## Classes

Classes in TypeScript are similar to those in ES6, but with additional features like modifiers.

```typescript
class Animal {
    name: string;
    constructor(name: string) {
        this.name = name;
    }
    move(distanceInMeters: number = 0) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}

let dog = new Animal("Dog");
dog.move(10);
```

---

## Functions

Functions in TypeScript can have typed parameters and return types.

```typescript
function add(x: number, y: number): number {
    return x + y;
}

let myAdd = function(x: number, y: number): number { return x + y; };
```

---

## Modules

Modules in TypeScript help organize code into reusable blocks.

```typescript
export class Calculator {
    static add(a: number, b: number): number {
        return a + b;
    }
}

import { Calculator } from './Calculator';

console.log(Calculator.add(2, 3));
```

---

## Generics

Generics provide a way to create reusable components.

```typescript
function identity<T>(arg: T): T {
    return arg;
}

let output = identity<string>("myString");
```

---

## Type Inference

TypeScript can automatically infer types based on the assigned values.

```typescript
let x = 3; // inferred to be number
```

---

## Advanced Types

TypeScript supports advanced types like intersection, union, and type guards.

```typescript
type NetworkLoadingState = {
    state: "loading";
};

type NetworkFailedState = {
    state: "failed";
    code: number;
};

type NetworkSuccessState = {
    state: "success";
    response: {
        title: string;
        duration: number;
        summary: string;
    };
};

type NetworkState =
    | NetworkLoadingState
    | NetworkFailedState
    | NetworkSuccessState;

function networkStatus(state: NetworkState): string {
    switch (state.state) {
        case "loading":
            return "Loading...";
        case "failed":
            return `Error ${state.code}`;
        case "success":
            return `Success: ${state.response.title}`;
    }
}
```

---

## Decorators

Decorators provide a way to add annotations and meta-programming syntax.

```typescript
function sealed(target: Function) {
    Object.seal(target);
    Object.seal(target.prototype);
}

@sealed
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}
```

---

## Conclusion

TypeScript is a powerful tool for JavaScript developers, providing type safety and enhanced features for building large-scale applications. With TypeScript, you can enjoy the benefits of both modern JavaScript and static typing.
