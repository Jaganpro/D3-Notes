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
```

We can append text in the DOM elements

```
d3.select('body').append('p').text('This is Appended Text');
```

### 3. Data Loading and Binding of Data in D3

In D3 we can display our DOM Elements using our Dataset. We can map Data into our DOM Elements.

In this example, we are using the dataset to loop through each datapoint and create a DOM element.


```
var dataset = [1, 2, 3, 4, 5];

d3.select('#D3OrgChartDiv') //Here we are selecting the Body of the DOM element
          .selectAll('p') // ??? This is needed, otherwise, it skips the first datapoint from the dataset. Don't know why.
          .data(dataset) //Choosing the dataset to loop though
          .enter() //Process one element at a time.
          .append('p') //Appends a Paragraph for each data element
          .text(function(d){ return d;});
```
 

















               
