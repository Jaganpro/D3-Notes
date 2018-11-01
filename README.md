# D3-Tutorial-Notes

### A) Selection of DOM Elements:

Using D3, we can select DOM elements. There are 2 methods to do this
```
  A. d3.select() --> Returns only the first element matching the criteria
  B. d3.selectAll() --> Returns all the elements matching the criteria
```
  
NOTE: They accept CSS Selectors or name of the Parameter and return the selection of the element.

Examples:
```
d3.select('h1');
```

### B) Manipulation of DOM Elements:

With D3 we can manipulate DOM Elements as well. 
This means we can update their Style, Values and Bind Data with them.

Example: Updating the color of the DOM Element
```
d3.select('h1').style('color','red');
```

We can chain multiple styles using the "Attr" method

```
d3.select('h1').style('color', 'red')
               .attr('class', 'heading');
```

If we want to update the text of the DOM Element, we can use the "text" property

```
d3.select('h1').text('Updated Text');


















               
