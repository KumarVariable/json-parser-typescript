# JSON Parser — Concepts & Architecture

### Goal: 

Build a standards-first JSON parser in TypeScript with:
- DOM
- streaming APIs
- strict-by-default behavior

---

### Introduction:

JSON (JavaScript Object Notation) is a lightweight data-interchange format used for exchanging or transfer data over the Internet.

#### Question 1. What JSON Document looks like ?

**Top Level**

- A JSON document is 1 value. It can be either any or all:

    - object `{...}`
    - array `[...]`
    - string `"text"`
    - number `42, -3.14, 1e6`
    - boolean `true / false`
    - null `null`

**Note:** Most APIs use an object or array at the top level, but any single value is allowed.

#### Question 2. What JSON Objects looks like ?

- Curly braces with **comma-separated** key–value pairs:
`{ "key": value, "another": value }`

- Rules:

    - Keys must be **double-quoted** strings.
    - `:` -> separates key and value.
    - Order is not guaranteed.
    - Duplicate keys are discouraged (parsers often keep the last one).

Example:

```json

{
    "id" : "A1234",
    "name" : "KUMAR",
    "isActive" : true,
    "contact" : 74567890,
    "tags": ["eng", "ai"],
    "profile": { "email": "nkunal@aol.com", "country": "India" }
}

```
#### Question 3. What JSON Arrays looks like ?

- Square brackets with **comma-separated** values:
`[ value1, value2, value3 ]`

- Values can be any JSON type (including nested arrays/objects).

Example

```json

[
    {"id" : 123, "name" : "KK"},
    {"id" : 898, "name" : "KumarK"}
]

```
#### Question 4. What counts as a JSON value ?

Exactly one of: object, array, string, number, true, false, null.

#### Question 5. Where is whitespace allowed and how is it treated ?

Spaces, tabs, and newlines are allowed between tokens and are ignored by parsers.

Inside strings, whitespace is part of the value

#### Question 6. What values, keys or types are not allowed in JSON ?

Not allowed in standard JSON:

- Comments `(// or /* */)`
- Trailing commas `([1,2,], {"a":1,})`
- Single quotes for strings or keys
- Unquoted keys `({ name: "Ada" })`
- Special numbers `(NaN, Infinity)`
- Leading zeros in numbers `(012)`

---

### Parsing

- The overall process of turning input text into a structured form your program can use.

- In a JSON parser, **parsing** means: `text → (tokens →) JS values/events`.

Mini-picture

```bash
"{"id":1}"  --parse-->  { id: 1 }
```










    




