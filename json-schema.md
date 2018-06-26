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
reference the JSON schema that the document adheres to. The JSON schema can be referenced locally, or using an HTTP URL. 

```js
{ 
  "$schema": "./local.schema.json"
}
```

```js
{
  "$schema": "http://json-schema.org/draft-07/schema"
}
```

### Specifying Data Type

A JSON schema document can specify the data type of a property using the `type` property. The property types are limited
to the following values:

* object 
* array 
* string
* number
* boolean
* null

The additional properties in the schema will depend on the data type specified.

