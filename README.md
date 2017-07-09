
Comments, unquoted keys, multi-line strings, trailing commas, optional commas, and more.

# JSON with Extensions (JSONX) or JSON v1.1 (a.k.a. JSON11 or JSON XI or JSON II) 

_JSON Evolved for Humans - Easy-to-Write, Easy-to-Read_


JSON v1.1 includes all JSON extensions from HanSON (JSON for Humans):

- quotes for strings are optional if they follow JavaScript identifier rules.
- you can alternatively use backticks, as in ES6's template string literal, as quotes for strings.
  A backtick-quoted string may span several lines and you are not required to escape regular quote characters,
  only backticks. Backslashes still need to be escaped, and all other backslash-escape sequences work like in
  regular JSON.
- for single-line strings, single quotes (`''`) are supported in addition to double quotes (`""`)
- you can use JavaScript comments, both single line (`//`) and multi-line comments (`/* */`), in all places where JSON allows whitespace.
- Commas after the last list element or object property will be ignored.

Plus all JSON extensions from SON (Simple Object Notation):

- comments starts with `#` sign and ends with newline (`\n`)
- comma after an object key-value pair is optional
- comma after an array item is optional


Example:

```
{
  #  use shell-like (or ruby-like) comments

  listName: "Sesame Street Monsters"   # note: comments after key-value pairs are optional  
  content: [
    {
      name: "Cookie Monster"
      // note: the template quotes and unescaped regular quotes in the next string
      background: `Cookie Monster used to be a
monster that ate everything, especially cookies.
These days he is forced to eat "healthy" food.`
    }, {
      // You can single-quote strings too:
      name: 'Herry Monster',
      background: `Herry Monster is a furry blue monster with a purple nose.
He's mostly retired today.`
    },    /* don't worry, the trailing comma will be ignored  */
   ]
}
```

same as "vanilla" ye old' JSON:

``` json
{
  "listName": "Sesame Street Monsters",       
  "content": [
    { "name": "Cookie Monster",
       "background": "Cookie Monster used to be a\n ... to eat \"healthy\" food."
    },
    { "name": "Herry Monster",
      "background": "Herry Monster is a furry blue monster with a purple nose.\n ... today."
    }
  ]
}
```


## Readers / Parsers

**Ruby**

- `json-next` library (github: [datatxt/json-next](https://github.com/datatxt/json-next))



## What's different?

### JSON5

JSON5 is a close relative. 

What's missing?

- `#`-comments 
- optional commas for object key-value pairs
- optional commas for array items
- single quoted strings


### HJSON

HJSON is a close relative.

What's different?

- HJSON use `"""` triple double quoted strings for multi-line strings; JSON v11 uses backticks for multi-line strings (like ES6)
- HJSON unquoted strings allow spaces and more; JSON v11 only allows identifiers for unquoted strings


### HanSON

HanSON is a subst. JSON v11 includes all HanSON extensions ;-)

### SON

SON is a subset. JSON v11 includes all SON extensions ;-)





## More JSON Formats

See the [Awesome JSON (What's Next?)](https://github.com/datatxt/awesome-json-next) collection / page.


## Meta

**License**

![](https://publicdomainworks.github.io/buttons/zero88x31.png)

The JSON with Extensions format is dedicated to the public domain. Use it as you please with no restrictions whatsoever.

**Questions? Comments?**

Post them to the [wwwmake forum](http://groups.google.com/group/wwwmake). Thanks!
