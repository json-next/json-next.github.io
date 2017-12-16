
[JSON: 1.1 # JSON with Extensions @ GitHub](https://github.com/json-next)


Comments • Unquoted strings • Multi-line strings • Folded strings • Trailing commas • Optional commas • `<..-..>` shortcuts • Optional `=` is the new `:` • Auto-wrapped objects • and more


# JSON: 1.1 # JSON with Extensions (JSONX) 

_JSON v1.1 - JSON Evolved for Humans - Easy-to-Write, Easy-to-Read_


## Welcome

_What's JSON with Extensions? Why? Why?_

JSON with Extensions (JSONX) - also known as JSON: 1.1, JSON v1.1, JSON11, JSON XI, or JSON II - is a 
new JSON format evolved for humans, that is,
the goal of the JSON extensions is making writing and reading JSON easier for you (dear human). 
JSON is no longer used as a machine-to-machine data interchange format only, thus, let's make it more human-friendly.



## Spec

_JSON v1.1 Format Specification in English_


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

Plus some more extra JSON extensions:

- unquoted strings following the JavaScript identifier rules can use the dash (`-`) too e.g. allows common keys such as `core-js`, `babel-preset-es2015`, `eslint-config-jquery` and others



Example:

``` text
{
  #  use shell-like comments

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

same ye old' "vanilla" JSON:

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


## Real-World Examples

_Code Libraries, Web Feeds, Tables & Schemas, Map Features, & More_

[package.json](#packagejson) •
[feed.json](#feedjson) •
[datapackage.json](#datapackagejson) •
[geojson](#geojson)


### package.json


**"Classic" Colon (:) Variant**

``` text
{
  name        :  jquery
  title       :  jQuery
  description : 'JavaScript library for DOM operations'
  version     :  3.2.2-pre
  main        :  dist/jquery.js
  homepage    : 'https://jquery.com'
  author      : {
    name : 'JS Foundation and other contributors'
    url  : 'https://github.com/jquery/jquery/blob/master/AUTHORS.txt'
  }
  repository  : {
    type :  git
    url  : 'https://github.com/jquery/jquery.git'
  }
  keywords    : [ jquery javascript browser library ]
  bugs        : {
    url  : 'https://github.com/jquery/jquery/issues'
  }
  license     : MIT
  dependencies    : {}
  devDependencies : {
    babel-preset-es2015  :  6.24.1
    commitplease         :  2.7.10
    core-js              :  2.4.1
    cross-spawn          :  5.1.0
    eslint-config-jquery :  1.0.1
    grunt                :  1.0.1
    grunt-babel          :  6.0.0
    grunt-cli            :  1.2.0
    ...
  }
  scripts : {
    build     : 'npm install && grunt'
    start     : 'grunt watch'
    test      : 'grunt && grunt test:slow'
    precommit : 'grunt lint:newer'
    commitmsg : 'node node_modules/commitplease'
  }
  commitplease : {
    nohook : true
    ...
  }
}
```

**"Alternate" Equals (=) Variant with Auto-Wrap**

``` text
name        =  jquery
title       =  jQuery
description = 'JavaScript library for DOM operations'
version     =  3.2.2-pre
main        =  dist/jquery.js
homepage    =  https://jquery.com
author      = {
  name = 'JS Foundation and other contributors'
  url  = https://github.com/jquery/jquery/blob/master/AUTHORS.txt
}
repository  = {
  type = git
  url  = https://github.com/jquery/jquery.git
}
keywords    = [ jquery javascript browser library ]
bugs        = {
  url  = https://github.com/jquery/jquery/issues
}
license     = MIT
dependencies    = {}
devDependencies = {
  babel-preset-es2015  =  6.24.1
  commitplease         =  2.7.10
  core-js              =  2.4.1
  cross-spawn          =  5.1.0
  eslint-config-jquery =  1.0.1
  grunt                =  1.0.1
  grunt-babel          =  6.0.0
  grunt-cli            =  1.2.0
  ...
}
scripts = {
  build     = 'npm install && grunt'
  start     = 'grunt watch'
  test      = 'grunt && grunt test:slow'
  precommit = 'grunt lint:newer'
  commitmsg = 'node node_modules/commitplease'
}
commitplease = {
  nohook = true
  ...
}
```

(Original Source: [jquery/jquery/package.json](https://github.com/jquery/jquery/blob/master/package.json))


### feed.json



**Simple - "Classic" Colon (:) Variant**

``` text
{
  version       : 'https://jsonfeed.org/version/1'
  title         : 'My Example Feed'
  home_page_url : 'https://example.org/'
  feed_url      : 'https://example.org/feed.json'
  items         : [
        {
            id           : '2'
            content_text : 'This is a second item.'
            url          : 'https://example.org/second-item'
        }
        {
            id           : '1'
            content_html : '<p>Hello, world!</p>'
            url          : 'https://example.org/initial-post'
        }
    ]
}
```

**Simple - "Alternate" Equals (=) Variant with (<..-..>) Shortcuts and Auto-Wrap**

``` text
version       = https://jsonfeed.org/version/1
title         = 'My Example Feed'
home_page_url = https://example.org/
feed_url      = https://example.org/feed.json
items         = 
< id           = '2'
  content_text = 'This is a second item.'
  url          = https://example.org/second-item
  -
  id           = '1'
  content_html = '<p>Hello, world!</p>'
  url          = https://example.org/initial-post
>
```


**Podcast - "Classic" Colon (:) Variant**

``` text
{
    version         : 'https://jsonfeed.org/version/1'
    user_comment    : 'This is a podcast feed. You can add this feed to your podcast client using the following URL: http://therecord.co/feed.json'
    title           : 'The Record'
    home_page_url   : 'http://therecord.co/'
    feed_url        : 'http://therecord.co/feed.json'
    items           : [
        {
            id    : 'http://therecord.co/chris-parrish'
            title : 'Special #1 - Chris Parrish'
            url   : 'http://therecord.co/chris-parrish'
            content_text : `Chris has worked at Adobe and as a founder of Rogue Sheep, 
                            which won an Apple Design Award for Postage. Chris's new company is Aged & Distilled 
                            with Guy English - which shipped Napkin, a Mac app for visual collaboration. 
                            Chris is also the co-host of The Record. He lives on Bainbridge Island, 
                            a quick ferry ride from Seattle.`
            content_html : `Chris has worked at <a href="http://adobe.com/">Adobe</a> and as a founder of Rogue Sheep,
                            which won an Apple Design Award for Postage. Chris's new company is Aged & Distilled
                            with Guy English - which shipped <a href="http://aged-and-distilled.com/napkin/">Napkin</a>, 
                            a Mac app for visual collaboration. Chris is also the co-host of The Record. 
                            He lives on <a href="http://www.ci.bainbridge-isl.wa.us/">Bainbridge Island</a>, 
                            a quick ferry ride from Seattle.`
            summary : 'Brent interviews Chris Parrish, co-host of The Record and one-half of Aged & Distilled.'
            date_published : '2014-05-09T14:04:00-07:00',
            attachments    : [
                {
                    url           : 'http://therecord.co/downloads/The-Record-sp1e1-ChrisParrish.m4a'
                    mime_type     : audio/x-m4a
                    size_in_bytes : 89_970_236
                    duration_in_seconds : 6_629
                }
            ]
        }
    ]
}
```


**Podcast - "Alternate" Equals (=) Variant with (<..-..>) Shortcuts and Auto-Wrap**

``` text
version         =  https://jsonfeed.org/version/1
user_comment    = 'This is a podcast feed. You can add this feed to your podcast client using the following URL: http://therecord.co/feed.json'
title           = 'The Record'
home_page_url   =  http://therecord.co/
feed_url        =  http://therecord.co/feed.json
items           =    
  < id            =  http://therecord.co/chris-parrish
    title         = 'Special #1 - Chris Parrish'
    url           =  http://therecord.co/chris-parrish
    content_text  = `Chris has worked at Adobe and as a founder of Rogue Sheep, 
                        which won an Apple Design Award for Postage. Chris's new company is Aged & Distilled 
                        with Guy English - which shipped Napkin, a Mac app for visual collaboration. 
                        Chris is also the co-host of The Record. He lives on Bainbridge Island, 
                        a quick ferry ride from Seattle.`
    content_html  = `Chris has worked at <a href="http://adobe.com/">Adobe</a> and as a founder of Rogue Sheep,
                        which won an Apple Design Award for Postage. Chris's new company is Aged & Distilled
                        with Guy English - which shipped <a href="http://aged-and-distilled.com/napkin/">Napkin</a>, 
                        a Mac app for visual collaboration. Chris is also the co-host of The Record. 
                        He lives on <a href="http://www.ci.bainbridge-isl.wa.us/">Bainbridge Island</a>, 
                        a quick ferry ride from Seattle.`
    summary        = 'Brent interviews Chris Parrish, co-host of The Record and one-half of Aged & Distilled.'
    date_published =  2014-05-09T14:04:00-07:00
    attachments    = 
    <  url           = http://therecord.co/downloads/The-Record-sp1e1-ChrisParrish.m4a
       mime_type     = audio/x-m4a
       size_in_bytes = 89_970_236
       duration_in_seconds = 6_629
    >
  >
```



## datapackage.json

_Tabular Data Package - Frictionless Data_

**"Classic" Colon (:) Variant**

``` text
{
  name      :  s-and-p-500-companies
  title     : 'S&P 500 Companies with Financial Information'
  license   :  PDDL-1.0
  resources : [
    {
      name:  constituents
      path: data/constituents.csv
      format: csv
      mediatype: text/csv
      schema: {
        fields: [
          { name: 'Symbol'  type: string  description: '' }
          { name: 'Name'    type: string  description: '' }
          { name: 'Sector'  type: string  description: '' }
        ]
      }
    }
    {
      name: constituents-financials
      path: data/constituents-financials.csv
      format: csv
      mediatype: text/csv
      schema: {
        fields: [
          { name: 'Symbol'          type: string  description: '' }
          { name: 'Name'            type: string  description: '' }
          { name: 'Sector'          type: string  description: '' }
          { name: 'Price'           type: number  description: '' }
          { name: 'Dividend Yield'  type: number  description: '' }
          { name: 'Price/Earnings'  type: number  description: '' }
          { name: 'Earnings/Share'  type: number  description: '' }
          { name: 'Book Value'      type: number  description: '' }
          { name: '52 week low'     type: number  description: '' }
          { name: '52 week high'    type: number  description: '' }
          { name: 'Market Cap'      type: number  description: '' }
          { name: 'EBITDA'          type: number  description: '' }
          { name: 'Price/Sales'     type: number  description: '' }
          { name: 'Price/Book'      type: number  description: '' }
          { name: 'SEC Filings'     type: string  format: url  description: '' }
        ]
      }
    }
  ]
}
```

**"Alternate" Equals (=) Variant with (<..+..>) Shortcuts and Auto-Wrap**

``` text
name      =  s-and-p-500-companies
title     = 'S&P 500 Companies with Financial Information'
license   =  PDDL-1.0
resources = 
< name =  constituents
  path = data/constituents.csv
  format = csv
  mediatype = text/csv
  schema = {
    fields = <  name = 'Symbol'  type = string  description = '' 
              + name = 'Name'    type = string  description = '' 
              + name = 'Sector'  type = string  description = '' 
             >
  }
  +
  name = constituents-financials
  path = data/constituents-financials.csv
  format = csv
  mediatype = text/csv
  schema = {
    fields = <  name = 'Symbol'          type = string  description = ''
              + name = 'Name'            type = string  description = '' 
              + name = 'Sector'          type = string  description = ''
              + name = 'Price'           type = number  description = '' 
              + name = 'Dividend Yield'  type = number  description = '' 
              + name = 'Price/Earnings'  type = number  description = '' 
              + name = 'Earnings/Share'  type = number  description = '' 
              + name = 'Book Value'      type = number  description = '' 
              + name = '52 week low'     type = number  description = '' 
              + name = '52 week high'    type = number  description = '' 
              + name = 'Market Cap'      type = number  description = '' 
              + name = 'EBITDA'          type = number  description = '' 
              + name = 'Price/Sales'     type = number  description = '' 
              + name = 'Price/Book'      type = number  description = '' 
              + name = 'SEC Filings'     type = string  format = url  description = '' 
             >
  }
>
```


(Original Source: [datasets/s-and-p-500-companies/datapackage.json](https://github.com/datasets/s-and-p-500-companies/blob/master/datapackage.json))


### geojson

**"Classic" Colon (:) Variant**

``` text
{
  type: FeatureCollection
  features: [
  {
        type: Feature
        geometry: {  type: Point  coordinates: [ 16.4780312  48.1397436 ]  }
        properties: {
          title        : 'Brauerei Schwechat (Brau Union)'
          description  : '2320 Schwechat // Mautner Markhof-Straße 11'
          city         : 'Schwechat'
          state        : 'Niederösterreich'
          web          :  www.schwechater.at
          type         : 'berwery (l)'
          marker-color : '#ff0000'
          marker-size  :  large
        }
  }
  {
        type: Feature
        geometry: {  type: Point  coordinates: [ 16.3725042  48.2083537 ]  }
        properties: {
          title        : '1516 Brewing Company'
          description  : '1010 Wien // Krugerstraße 18/Schwarzenbergstraße 2'
          city         : 'Wien'
          state        : 'Wien'
          web          :  www.1516brewingcompany.com
          type         : 'brewpub'
          marker-color : '#ffa500'
          marker-size  :  small
       }
  }
  ...
  ]
}  
```


**"Alternate" Equals (=) Variant with (<..-..>) Shortcuts and Auto-Wrap**

``` text
type     = FeatureCollection
features =
< type     = Feature
  geometry = { type = Point  coordinates = [ 16.4780312  48.1397436 ]  }
  properties = {
    title        = 'Brauerei Schwechat (Brau Union)'
    description  = '2320 Schwechat // Mautner Markhof-Straße 11'
    city         = 'Schwechat'
    state        = 'Niederösterreich'
    web          =  www.schwechater.at
    type         = 'berwery (l)'
    marker-color = '#ff0000'
    marker-size  =  large
  }
  -
  type     = Feature
  geometry = { type = Point  coordinates = [ 16.3725042  48.2083537 ]  }
  properties = {
    title        = '1516 Brewing Company'
    description  = '1010 Wien // Krugerstraße 18/Schwarzenbergstraße 2'
    city         = 'Wien'
    state        = 'Wien'
    web          =  www.1516brewingcompany.com
    type         = 'brewpub'
    marker-color = '#ffa500'
    marker-size  =  small
  }
  ...
>  
```

(Original Source: [beerbook/maps/at/at.geojson](https://github.com/beerbook/maps/blob/master/at/at.geojson))



## Readers / Parsers

[Ruby](#ruby)

### Ruby

**`json-next`** library (github: [json-next/json-next](https://github.com/json-next/json-next)) - Use `JSONX.convert` or `JSONXI.convert` or `JSON11.convert` to convert to plain "vanilla" ye old' JSON. Use `JSONX.parse` or `JSONXI.parse` to convert to hash, array, etc. Note: `JSONX.parse` is the same as `JSON.parse( JSONX.convert( text ))`




## Tests, Tests, Tests


"Official" Test Suite (github: [jsonx @ json-next/json-next-tests](https://github.com/json-next/json-next-tests/tree/master/jsonx))  - includes tests for package.json, feed.json, datapackage.json, geojson, and more



## What's different?

[JSON5](#json5) •
[HJSON](#hjson) •
[HanSON](#hanson) •
[SON](#son)

### JSON5

JSON5 is a close relative. 

What's missing?

- `#`-comments 
- optional commas for object key-value pairs
- optional commas for array items
- mulit-line strings with backticks (ES6-like)

What's different?

- allows dash (`-`) in javascript identifiers e.g. `core-js`, `babel-preset-es2015`, `eslint-config-jquery` and others
- allows underscores (`_`) in numbers e.g. `1_000_000` (instead of `10000000`)  -- FUTURE ADDITION


### HJSON

HJSON is a close relative.

What's different?

- HJSON uses `"""` triple double quoted strings for multi-line strings; JSON v11 uses backticks for multi-line strings (like ES6)
- HJSON unquoted strings allow spaces and more (until the end of line); JSON v11 only allows identifiers for unquoted strings


Note:  JSONX with Extension will add `"""` and `'''` as (alternative) multi-line strings -- FUTURE ADDITION



### HanSON

HanSON is a subset. JSON v11 includes all HanSON extensions ;-)

### SON

SON is a subset. JSON v11 includes all SON extensions ;-)





## More JSON Formats

See the [Awesome JSON (What's Next?)](https://github.com/json-next/awesome-json-next) collection / page.


## Meta

**License**

![](https://publicdomainworks.github.io/buttons/zero88x31.png)

The JSON with Extensions format is dedicated to the public domain. Use it as you please with no restrictions whatsoever.

**Questions? Comments?**

Post them to the [wwwmake forum](http://groups.google.com/group/wwwmake). Thanks!
