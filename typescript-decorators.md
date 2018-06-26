# TypeScript Decorators

## Documentation

* [TypeScript Handbook](http://www.typescriptlang.org/docs/handbook/decorators.html)

## Usage

TypeScript decorators are applied using the syntax `@DecoratorName()`. Decorators can be applied to class declarations, 
methods, accessors, properties, or parameters. 

Multiple decorators can be applied to a single component. They will be resolved in reverse order. For instance, `@A() @B()` 
will resolve decorator B first, and then A.

Decorators are applied in the following order:

1. Instance parameters
2. Instance methods
3. Instance accessors
4. Instance properties
5. Static parameters
6. Static methods
7. Static accessors
8. Static properties
9. Constructor parameters
10. Class

## Implementation

TypeScript decorators are implemented as functions. The name of the function specifies the name following the @ symbol.

Decorators may either be applied directly to the decorated component

```ts
function DecoratorName(target) {
  // Process target
}

@DecoratorName() 
```

or as a factory returning the decorator function.


```ts
function DecoratorName(arg1, arg2) {
  return function(target) {
    // Process target with arguments
  }
}

@DecoratorName('hello', 'world')
```

### Property Decorators

Property decorators take the target (class containing the property), the propery key, and the property descriptor.

```ts
function PropertyDecorator(target, propertyKey: string, descriptor: PropertyDescriptor) {

}
```
