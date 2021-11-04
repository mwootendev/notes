# Reflect Metadata

## Official Documentation

* [Github Page](https://github.com/rbuckton/reflect-metadata)
* [NPM Page](https://www.npmjs.com/package/reflect-metadata)

## Overview

The reflect-metadata package is used to record metadata about types. It is most commonly used with TypeScript decorators to 
record and use metadata about properties and parameters.

## API

### Declaring Metadata

Metadata is declared using the `Reflect.defineMetadata()` method. The method accepts a metadata key representing the metadata 
being stored. This is usually a `Symbol` specific for the metadata. The method also accepts the value of the metadata, and the 
target for which the metadata is being recorded. The target can either be a constructor function or a class prototype object.
If the metadata is specific to a property in the target, the property key can also be provided.

```ts
Reflect.defineMetadata(metadataKey, metadataValue, target);
Reflect.defineMetadata(metadataKey, metadataValue, target, propertyKey);
```

### Retrieving Metadata

Metadata is retrieved using the `Reflect.getMetadata()` method. The method accepts the metadata key used to store the metadata, 
and the target for which the metadata value was stored. If the metadata is related to a specific property of the target, 
the propertyKey can also be provided.

```ts
let metadataValue = Reflect.getMetadata(metadataKey, target);
let metadataValue = Reflect.getMetadata(metadataKey, target, propertyKey);
```
