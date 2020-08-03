# Angular Schematics

## Tools

### Schematics CLI

The Schematics CLI provides the `schematics` command, which is similar to Angular's `ng generate` command, but is not dependent on Angular. The tool can be used to create new schematics.

#### Installation

```bash
npm install @angular-devkit/schematics-cli
```

#### New Project

```bash
schematics blank $name
```

## Project Structure

- .gitignore
- .npmignore
- package-lock.json
- package.json
- README.md
- src
  - collection.json
  - $name
    - index_spec.ts
    - index.ts
- tsconfig.json

### collection.json

The `collection.json` file contains the definitions of all of the schematics available in the project. These are the commands that will be available to tools such as `ng generate`. 

The file is structured as follows:

```json
{
  "$schema": "../node_modules/@angular-devkit/schematics/collection-schema.json",
  "schematics": {
    "$schematic_name": {
      "description": "A description of the schematic",
      "factory": "./$name/index#$schematic_name",
      "schema": "./$name/schema.json"
    }
  }
}
```

## Schematic Concepts

### Schematic Factory

A schematic factory is a factory simply designed to return the appropriate Rule. The factory is provided with any options specified for the schematic. The factory is named after the schematic, and this is the name that will be
referenced in `colletion.json`.

```javascript
export function $schematic_name(_options: any): Rule {
    return ...;
}
```

The options correspond to the flags provided when calling the schematic. For instance:

```bash
schematic .:$schematic_name --option-one=thing1 --two=thing2
```

will result in the following options:

```json
{
  "optionOne": "thing1",
  "two": "thing2"
}
```

#### Schematics Options

The options can be specified using a `schema.json` file alongside the source for the schematic.

```json
{
  "$schema": "http://json-schema.org/schema",
  "id": "$nameOptions",
  "title": "$name Options Schema",
  "type": "object",
  "description": "Options for the $name schematics",
  "properties": {
    "optionName": {
      "type": "string",
      "description": "Description of option",
      "$default": {
        "$source": "argv",
        "index": 0
      },
      "x-prompt": "Prompt for the option"
    }
  },
  "required": [
    "optionName"
  ]
}
```

Additionally, a TypeScript `.d.ts` definition file can be used to specify the options and replace the type of `any` in the factory function.

The `dtsgenerator` package can be used to automatically generated the `.d.ts` file from the `schema.json` file.

```sh
dtsgen path/to/schema.json -o path/to/schema.d.ts
```

 ### Rule

 A schematic Rule is a Function that accepts the project Tree and a schematic context, applies some transformations on the Tree, and returns the updated Tree.

 ```javascript
(tree: Tree, _context: SchematicContext) => {
    // Changes to tree
    return tree;
}
 ```

 ### Tree

 A schematic Tree is the virtual representation of the project's files. Changes are made to the virtual Tree. This allows for previewing changes and only committing changes if the entire schematic is successful.

## Schematic Operations

All operations are performed on the Tree. 

### Create a File

`Tree.create(filename, content)` provides a means to create a new file and specify its content.

### Load Template Local Files

The `url()` utility is used to reference local files included with the template. For instance, for local files included with the template in a `files` directory, the following could be used to get a refernce to the files.

```typescript
const localFiles = url('./files');
```

### Using Templates

Templates can have variables replaced using the `template()` function.

#### Template Naming

Template names can include variables prefixed with a __ (double underscore). Example: `__name__.json`.

Template names can also use functions applied to names to convert parts of the filename. For instance `thing-__name__@dasherize__.json` would result in a kebab-case version of the name.

The schematics library includes built in functions, which convert a string to another format.

* classify - converts strings to UpperCamelCase format used for class names.
* camelize - converts string to lowerCamelCase format for variable or parameter names.
* dasherize - converts strings to dash-separated format for file names.
* underscore - converts strings to snake_case format.

Additional functions can be supplied as an additional parameter to the `template()` function.

```typescript
template({
  varName: 'value',
  transformFunction
})
```

#### Template Variables

Schematics variables can be substituted using the `<%= %>` syntax. Example: `<%=name %>` would replace the variable with the option value of the name.

Functions can also be used inside `<%= %>` to transform the variables. `my-<%=classify(name) %>` would convert the name to a class delcaration format, for instance.

#### Advanced Template Logic

Templates support use of JavaScript statements like `if` or `for` within `<% %>` blocks. 

```
<% if (condition) { %>
  conditional code
<% } else { %>
  alternate condition
<% } %>
```

### Common Schematic Functions

#### normalize()

#### chain()

#### branchAndMerge()

#### mergeWith()

#### apply()

```typescript
apply (source: Source, rules: Rule[]): Source;
```


## Building

```bash
npm run build
```

### Watching for Changes

The following can be added to the `scripts` section of `package.json` to watch for changes and rebuild.

```json
"build:watch": "tsc -p tsconfig.json --watch"
```

## Running

The `schematics` command can be used with the name of the package (or a relative directory), a colon, and the name of the schematic. 

```bash
schematic $name:$schematic_name
# or
schematic .:$schematic_name
# or
schematic ../$name/src/collection.json:$schematic_name
```

Schematics run in the local directory will be run in dry-run mode. This can be disabled with `--debug=false` or `--dry-run=false`. 

## Testing

### SchematicTestRunner

### UnitTestTree

## Links

* [@angular-devkit/schematics NPM Page](https://www.npmjs.com/package/@angular-devkit/schematics)
* [@angular-devkit/schematics Git Repository](https://github.com/angular/angular-cli/tree/master/packages/angular_devkit/schematics)
* [Angular Blog Schematics Introduction](https://blog.angular.io/schematics-an-introduction-dc1dfbc2a2b2)
* [Total Guide to Custom Angular Schematics](https://medium.com/@tomastrajan/total-guide-to-custom-angular-schematics-5c50cf90cdb4)
