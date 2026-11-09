## Introduction



Union types are used to assign a variable with multiple types of values. Using Type Narrowing we can check the value of a variable and limit the possible types it can be within a specific block of code. This allows TypeScript to ensure operations will be safe without the need for any 'any' types.

## Deep Dive



A 'typeof' check can be used with primitive types e.g. strings, numbers and booleans. As TypeScript knows what the condition is it can narrow down the variable.



```ts

function formatValue(value: string | number): string {

if (typeof value === "string") {

return value.trim().toLowerCase();

}



return value.toFixed(2);

}

```



The 'instanceof' check can be used to see if an object was instantiated from a specific class/constructor. This is useful when dealing with classes.



```ts

class Dog {

bark(): string {

return "Woof";

}

}



function speak(value: Dog | Date): string {

if (value instanceof Dog) {

return value.bark();

}



return value.toDateString();

}

```



The 'in' check can be used to see if a property exists on an object. This can be used to differentiate between objects with different properties.



```ts

type Admin = { permissions: string[] };

type Member = { email: string };



function describeUser(user: Admin | Member): string {

if ("permissions" in user) {

return user.permissions.join(", ");

}



return user.email;

}

```



All of these will give us some useful information to the compiler about what type our value is.



## Conclusion



Type Narrowing can make using union types safe and practical. Using 'typeof' with primitive types, 'instanceof' with class instances and 'in' with object properties will make your code more readable and avoid any errors at run time.