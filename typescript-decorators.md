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

### Class Decorators

Declared on a class itself. The decorator function is applied to the constructor, and it can be used to override the class declaration. A class decorator receives a single parameter, which is the constructor of the class. 

```ts
function ClassDecorator(constructor: Function) {
  // Do something with constructor
}
```

If the decorator function returns a Function or another class, that will be used to override the class being decoratored.

```ts
function ClassDecorator<T extends {new(...args:any[]):{}}>(constructor:T) {
    return class extends constructor {
        // Update class with additional properties, etc.
    }
}
```

### Method Decorators

Applied to the property descriptor of a method. The method declaration can be replaced by returning a new property descriptor. 

#### Static Methods

The target of the decorator will be the constructor function of the class defining the static method.

```ts
function StaticMethodDecorator(constructor: Function, propertyKey: string, property: PropertyDescriptor) {
  
}
```

#### Instance Methods

The target of the decorator will be the Object prototype of the method's instance.

```ts
function InstanceMethodDecorator(prototype: Object, propertyKey: string, property: PropertyDescriptor) {
  
}
```

### Accessor Decorators

Must be applied to either the `get` or `set`, but cannot be applied to both. The decorator should be applied to the whichever accessor is applied first.

#### Static Accessors

The target of the decorator will be the constructor function of the class defining the static method.

```ts
function StaticAccessorDecorator(constructor: Function, propertyKey: string, property: PropertyDescriptor) {
  
}
```

#### Instance Accessors

The target of the decorator will be the Object prototype of the method's instance.

```ts
function StaticMethodDecorator(prototype: Object, propertyKey: string, property: PropertyDescriptor) {
  
}
```

### Property Decorators

Declared before class properties (fields). The decorator will receive the name of the field, but not a property descriptor. Property decorators can only be used to store metadata about a property, but cannot make any changes. Another library, such as reflect-metadata, can be used to store metadata about the property for use by other functions or decorators.

#### Static Properties

The target of the decorator will be the constructor of the class declaring the static property.

```ts
function StaticPropertyDecorator(constructor: Function, propertyKey: string) {
  // Record metadata about property
}
```

#### Instance Properties

The target of the decorator will be the prototype of the Object declaring the property.

```ts
function InstancePropertyDecorator(prototype: Object, propertyKey: string) {
  // Record metadata about property
}
```

#### Saving Property Metadata

```ts
import 'reflect-metadata';

const PROPERTY_METADATA = Symbol('PropertyName');

function PropertyDecorator(construcorOrPrototype: Function | Object, propertyKey: string) {
  Reflect.metadata(PROPERTY_METADATA, propertyKey);
}
```
