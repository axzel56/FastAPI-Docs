Beautiful Soup is a python library for pulling data out of HTML and XML Files.

## Kinds of Objects in Beautiful Soup

Beautiful Soup Transforms a complex HTML document into a tree of Python objects.
Types of objects:
- Tag
- NavigableString
- BeautifulSoup
- Comment

These objects represent the HTML elements that comprise the page.

## class Tag

A Tag object corresponds to an XML or HTML Tag in the original document.
```python
soup = BeautifulSoup('<b class="boldest"> BOLD TEXT </b>')
tag = soup.b
type(tag)

#excalidraw 
<class 'bs4.element.Tag'>
```

#### name
tag.name

#### attrs
`tag['id']`

```python
tag.attrs
# {'id' : 'boldest'}

tag.attrs.keys()
# dict_keys(['id'])
```
```python
MULTI_VALUED_ATTRIBUTES = {
    '*': ['class', 'rel', 'rev', 'accept-charset', 'headers', 'accesskey', 'sandbox'],
    'a': ['ping'],
    'link': ['ping'],
    'iframe': ['sandbox'],
    'object': ['archive'],
    'form': ['accept-charset'],
}
```

### class NavigableString

A tag can contain strings as pieces of text. Beautiful Soup uses the NavigableString class to contain these pieces of text.
