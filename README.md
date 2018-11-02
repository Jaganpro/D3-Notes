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

### C) Data Loading and Binding of Data in D3

In D3 we can display our DOM Elements using our Dataset. We can map Data into our DOM Elements.

In this example, we are using the dataset to loop through each datapoint and create a DOM element.


```
var dataset = [1, 2, 3, 4, 5];

d3.select('#D3OrgChartDiv') //Here we are selecting the Body of the DOM element
          .selectAll('p') // ??? This is needed, otherwise, it skips the first datapoint from the dataset. Don't know why.
          .data(dataset) //Choosing the dataset to loop though . This will put the dataset in waiting state for further processing
          .enter() //Process one data item at a time.
          .append('p') //Appends a Paragraph for each data item
          .text(function(d){ return d;});
```
 
### D) Creating a Simple Bar Chart using D3.JS

We have variables which defines the height and width of the container

```
var dataset = [80, 100, 56, 120, 180, 30, 40, 120, 160];

var svgWidth = 500;
var svgHeight = 300;
var barPadding = 5;
var barWidth = (svgWidth / dataset.length);

var svg = d3.select('svg')
            .attr("width", svgWidth)
            .attr("height", svgHeight)
            
var barChart = svg.selectAll("rect")
                  .data(dataset)
                  .enter()
                  .append("rect")
                  .attr("y", function(d) {
                      return svgHeight - d
                  })
                  .attr("height", function(d) {
                      return d;
                  })
                  .attr("width", barWidth - barPadding)
                  .attr("transform", function(d, i) { 
                      var translate = [barWidth * i, 0];
                      return "translate(" + translate +")";
                  });

// We dont want all the bars in the bar chart to start from the same position. Hence we use the "Transform" [or] translate to describe where consecutive bars should start/

```














               
