# Notes

Add more syntax alternatives and shortcuts - why? why not?


## "Unrolled" Array Items

Instead of 

```
items : [
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
```

use

```
item id: '2' {
            content_text : 'This is a second item.'
            url          : 'https://example.org/second-item'
        }
        
item id: '1' {
            content_html : '<p>Hello, world!</p>'
            url          : 'https://example.org/initial-post'
        }
```


or with "implied" ids

```
item '2' {
            content_text : 'This is a second item.'
            url          : 'https://example.org/second-item'
         }
        
item '1' {
            content_html : '<p>Hello, world!</p>'
            url          : 'https://example.org/initial-post'
         }
```

