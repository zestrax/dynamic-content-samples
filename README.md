# Amplience Dynamic Content
Amplience Dynamic Content is a headless CMS specifically designed to support online retailers deliver content to all of their digital channels.  Content is delivered through a web service as JSON and the shape of the JSON is defined using a Content Type which is basically a Schema which follows the [JSON Schema.org standard](http://json-schema.org/).  Content in Amplience can be modularised into smaller componments which themselves are content types defined using schemas.  This method allows you to model very sophisicated content types from reusable components.  As Amplience Content types fully adhere to JSON schema it is possible to use schema development tools such as Liquid XML Studio and XMLspy.

# Content Type Libraries

Content types that are used as reusable components can be organized into Type Libraries which are JSON Schema documents where the component schemas are held within a definitions section.

```
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "type": "object",
    "title": "Core type schema for links",
    "description":"Core content type components to build content types",
    "id": "link-content-type-library.json",
    "definitions": {
      "fixed-link": {
        "type": "object",
        "title": "URL LINK",
        "properties": {
            "text": {
                "type": "string",
                "maxLength": 155,
                "title": "Link Title",
                "format": "text"
            },
            "url": {
                "type": "string",
                "title": "Url",
                "description": "an absolute fully qualified url",
                "format": "uri"
            }
          }
        }    
     }
}
```
# Complex Content Types
Once you have your reusable content type components organised into libraries you can create complex Types by simply referenceing your Type Library and Component Content Type using standard JSON Schema notation.
**E.G**
```
"callToAction": {
  "$ref": "../component-libraries/links-content-type-library.json#/definitions/relative-link"
        }
```
Referencing component libriries has the effect of nesting the Content Type component in the UI
![Link content type Amplience UI snippet](http://i1.adis.ws/i/jwdemo/link-content-type-UI-snip)

# Type Libraries
Sample type libraries for representing common components for building more complex content types

*alignment-content-type-library.json* 

- v-align - selecting left, right and center   
- h-align - selecting top, bottom and middle
- alignment - selecting horitzontal and vertical alignment

*links-content-type-library*

- relative-link - provides fields for relative link /../../...com link text and define styling classes
- fixed-link - provides fields for fully qualified url, link text and define styling classes

*color-content-type-library*

- web-color - selection of web colors e.g. red Maroon green
- color-code - color code e.g. fff, ffffff

*opacity-content-type-library*

- transparency-list - selection of transparency value 10,20,30....
- transparency-value - field accepting integer 0-100
- opacity-value- field accepting number 0 -1

*positioning-content-type-library*

- positioning-top-left - set the position using top and left
- positioning-bottom-right - set the position using bottom and right

*text-content-type-library*

- aligned-text - fields for text entry and setting alignment
- aligned-text-block - array of aligned-text components, and the ability to set position using alignment component (e.g. left middle), background color, transparency, and text color
- positioned-text-block - array of aligned-text components, and the ability to set position using  positioning-top-left component (e.g. 10,10), background color, transparency, and text color

*text-css-styled-content-type-library*

- css-class-styled-text - fields for text entry and setting CSS classes
- aligned-styled-text-block - array of css-class-styled-text components, and the ability to set position using alignment component (e.g. left middle) and block CSS classes
- positioned-styled-text-block - array of css-class-styled-text components, and the ability to set position using  positioning-top-left component (e.g. 10,10),and block CSS classes#

# Complex Content Types

- image-banner-1 - set background image, array of upto 5 positioned-styled-text-block text block content type components and call to action link
- image-banner-2 - set background image, array of upto 5 positioned-text-block text block content type components and call to action link


# Handlebars Partials

