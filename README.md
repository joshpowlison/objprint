# objprint

Share info on your JS objects. Great for API test pages and the like.

You can see it being used live with [Ferret](https://ferret.heybard.com/).

# Setup

1. Load in JS and CSS files.
2. Create a new ObjPrint() object. You must pass it `window` and `explanationWindow` elements, or else it will throw errors. You can also pass it `properties` at this time or later on.
3. run the `print()` function on your `ObjPrint()` object, passing it the object you want to print out.

# Example
```js
var printer=new ObjPrint({
  window:document.getElementById("object"), // The element the object will be printed into
  explanationWindow:document.getElementById("explanation"), // The element the explanation will be printed into
  properties:{ // A list of explanations for various properties
    'normal':'This will display for a property called normal.'
    ,'parent':'This will display for a property called parent.'
    ,'parent.child':'This will display for property child of object parent.'
    ,'parent.*':'This will display for all children of object parent. * is a wildcard for any value.'
    ,'arr':'This will display for a property called arr.'
    ,'arr.#':'This will display for all instances in an array called arr. # is a wildcard for any array index.'
    ,'func':'This will display for a property called func.'
    ,'func(firstParam)':'This will display for the parameter called firstParam for a function called func.'
    ,'func(secondParam)':'This will display for the parameter called secondParam for a function called func.'
  },
  unsetAction:'default' // Can be 'default' or 'hide'. If 'hide', any property without information to call on will be hidden.
});

var objToPass={
  normal:'This is a property.',
  parent:{
    'child':'This is a child of a parent object.',
    'otherChild':'This is another child.',
    'forgottenChild':'This is yet another child.'
  },
  arr:[
    'First item',
    'Second item',
    'Third item'
  ],
  func:function(firstParam,secondParam){}
};

printer.print(objToPass);
```
