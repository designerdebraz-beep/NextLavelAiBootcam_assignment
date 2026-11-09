# Type Aliases vs Interfaces in Typescript

## Intro

TypeScript has two ways to define types within your code, the `type` and `interface` keywords. Whilst they can appear very similar there are some differences in their capabilities. Using the correct option will help keep your code maintainable and clear.

## Detailed

Interfaces are used mostly to define the shape of an object, however they can be extended using the `extends` keyword. You can define an interface which extends another interface to have the properties of the original interface. They can also be merged using declaration merging. This can be useful if you want to extend types from a library or create an API that can be used by plugins.

```ts

interface User {

id: number;

name: string;

}

interface Admin extends User {

permissions: string[];

}

```

A type alias can be used to do more than just define an objects shape. You can define unions, intersections, primitive types, tuples and function types. However they can’t be merged like interfaces, you can however merge types using operators like `|` and `&`.

```ts

type Status = "pending" | "success" | "error";

type UserWithRole = User & {

role: string;

};

```

Both can be used to define the properties of an object, and can be used with classes using `implements`. Neither will be better in all situations, it depends on your design.

## Conclusion

If you are trying to model an object structure that might get extended or merged then use an interface. If you are trying to create unions, intersections, tuples or any other type expressions then use a type. It is also important to have a consistent convention within your team as both give great static checking.