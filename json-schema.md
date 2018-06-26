# JSON Schema

## Links

* [Official Site](http://json-schema.org/)
* [Specification](http://json-schema.org/specification.html)

## Description

JSON Schema is a specfication for providing a schema for JSON documents in the forms of a JSON document itself. JSON
schema documents can specify limitations on the structure and data types of JSON documents, and can be used to validate
that JSON documents adhere to the schema. JSON schema documents use the MIME-Type `application/schema+json`.

## JSON Schema Document

JSON documents can reference a schema by including a `$schema` property in the document. The `$schema` property should 
reference the JSON schema that the document adheres to. The JSON schema can be referenced locally, or using a URI. A JSON schema document should provide its own `$id` URI to uniquely reference the schema being declared.

```js
{ 
  "$schema": "./local.schema.json"
}
```

```js
{
  "$schema": "http://json-schema.org/draft-07/schema",
  "$id": "http://www.example.com/example-schema.json"
}
```

JSON schema documents are composed of properties representing assertions and annotations. Assertion properties, such as type, 
resolve to a boolean condition that can be used for validation. Annotation properties, such as title, are used to provide
information to the users of the schema.

The root of the JSON schema document should include an `$id` 

### Specifying a Schema Name

Individual JSON schema levels can be given a name using the `title` property. 

```js
{
  "title": "name"
}
```

### Providing Documentation for Schema Properties

JSON schema properties can include a `description` to describe the property. 

Additionally, examples of the use of the schema can be added by using the `examples` property. The property accepts an array
of JSON objects as examples.

```js
{
  "title": "name",
  "description": "The first name of the person.",
  "examples": [
    {
      "name": "John Doe"
    }
  ]
}
```

### Providing a Default Value

The `default` property can be specify a default value for a property.

### Specifying Data Type

#### Basic Data Types

A JSON schema document can specify the data type of a property using the `type` property. The property types are limited
to the following values:

* object 
* array 
* string
* number
* boolean
* null

The type can either be a single string value from the list above, or an array referencing multiple values.
The additional properties in the schema will depend on the data type specified.

```js
{
  "type": "string"
}
```

#### Enumeration Data Types

A JSON schema document can specify a property to have an enumerable value using the `enum` property. An enumeration is an
array of possible values for the field, which may include `null`. The field is required to have one of the values specified in the array.

```js
{
  "enum": [ "red", "green", "blue", null]
}
```

#### Constant Data Types

A JSON schema document can enforce that a property have a single, specfic value using the `const` property.

```js
{
  "const": "42"
}
```

### Specifying Object Data Types

#### Specifying Properties

`properties` - { [string]: Schema }

`patternProperties` - { [RegEx]: Schema }

`additionalProperties` - { [string]: Schema }

#### Requiring Properties

`required` - array of property names that are required

#### Limiting Object Size

`maxProperties` - number

`minProperties` - number

### Specifying Array Data Types

#### Specifing Item Types

A JSON schema document can limit an array type to containing a specific data type or array of data types. The items are limited using the `items` property, which contains a schema for the item types or an array of schemas.

```js
{
  "items": [  ]
}
```

#### Bounds on Array Size

`minItems` - number

`maxItems` - number

#### Requiring Unique Elements

`uniqueItems` - boolean

#### Requiring Specific Elements

`contains` - Schema

### Limiting Numeric Values

#### Minimum Value

#### Maximum Value

#### Divisible By

### Limiting String Values

#### String Length

#### Matches Pattern

#### String Data Representations

##### Serialized Data Types

`format`

##### Encoded Data

`contentEncoding`

`contentMediaType`
