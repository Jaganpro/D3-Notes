# D3-Tutorial-Notes

D3 -- Data Driven Documents
      Used to easily Visualize and Interact with Data
      
In D3, there is lot of creativity. There is lot of ways we can analyze and express data.
      
### Prominent Examples of D3:

2013 Obama Budget Proposal : https://archive.nytimes.com/www.nytimes.com/interactive/2012/02/13/us/politics/2013-budget-proposal-graphic.html?hp

Who will win the Presidency? : https://projects.fivethirtyeight.com/2016-election-forecast/

Is it Better to Rent or Buy? : https://www.nytimes.com/interactive/2014/upshot/buy-rent-calculator.html

### A) Selection of DOM Elements: (DOM Traversal)

Using D3, we can select DOM elements. There are 2 methods to do this
```
  A. d3.select() --> Returns only the first element matching the criteria
  B. d3.selectAll() --> Returns all the elements matching the criteria
```

Examples:
```
d3.select('h1'); --> Using HTML Elements
d3.select('.cssClassName'); --> Using CSS Class Name
d3.select('#myDiv'); --> Selection Using ID
```

### B) Manipulation of DOM Elements:

With D3 we can manipulate DOM Elements using various functions. 

There are 3 main functions to do this
    A. d3.select('p').attr
    B. d3.select('p').style
    C. d3.select('p').append
    d. d3.select('p').text
    
Using "attr" We will be able to change the attributes of the HTML Element
```
d3.select('p').attr('class', 'heading');
```

Using "style", we would be able to change the css of the HTML Element.

```
d3.select('h1').style('color','red');
```

Using "append", we would be able to add the elements inside of the HTML Tags

```
d3.select('body').append('p').text('This is Appended Text');
```

If we want to update the text of the DOM Element, we can use the "text" property

```
d3.select('h1').text('Updated Text');
```

We can chain multiple functions using the dot notation.

```
d3.select('h1').style('color', 'red')
               .attr('class', 'heading');
```

### C) Handling DOM Events in D3

We can use DOM Events in D3

```
d3.selectAll('.hover-me')
  .on('mouseover', function(){
      this.style.backgroundColor = 'Red'
  })
  .on('mouseleave', function(){
      this.style.backgroundColor = '';
  })
```

### D) Data Loading and Binding of Data in D3

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
 
### E) Creating a Simple Bar Chart using D3.JS

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

// Here im Translate array, we describe the translate for X Axis (barWidth * i) and Y Axis (0).
// Here i is the Index.

```

### F) Creating Labels

Here we are trying to add Labels to each of the Bar Chart

```
var text = svg.selectAll("text")
              .data(dataset)
              .enter()
              .append("text")
              .text(function(d){
                  return d;
              })
              .attr("y", function(d, i){
                  return svgHeight - d - 2;
              })
              .attr("x", function(d, i){
                  return barWidth * i;
              })
              .attr("fill", "#A64C38");
```

### G) Scales in D3

Scales are functions which will transform our data, either by increasing or decreasing value for better visualizations.

Lets say our dataset = [1, 2, 3, 4, 5]
When we generate the barChart, it won't look good as the bars are barely visible

For this we are going to create a variable called "yScale" and we are going to call the function "d3.scaleLinear()"

```
var yScale = d3.scaleLinear()
               .domain([0, d3.max(dataset)])
               .range([0, svgHeight]);

```
### H) Axes in D3
Axes are made of Lines, Text and hence they are very complex.
Thankfully D3 provides us with various functions to create these

```
1. d3.axisTop()
2. d3.axisRight()
3. d3.axisBottom()
4. d3.axisLeft()
```


### I) Creating SVG Elements in D3

SVG - Scalable Vector Graphics

Let's say if we want to draw a line, then we can use the (X1,Y1) and (X2,Y2) Coordinates

```
var line = svg.append("line")
              .attr("x1", 100)
              .attr("y1", 50)
              .attr("x2", 500)
              .attr("y2", 50)
              .attr("stroke", "red")
              .attr("stroke-width", 5)
              
```
For Rectangle, we have to provide X and Y Co-ordinates, Height and Width.

```
var Rect = svg.append("rect")
              .attr("x", 100)
              .attr("y", 100)
              .attr("width", 200)
              .attr("height", 100)
              .attr("fill", "#9B95FF");
```
For Circle, we need to provide the co-ordinates of the center of the circle and its radius
  
```
var circle = svg.append("circle")
                .attr("cx", 200)
                .attr("cy", 300)
                .attr("r", 80)
                .attr("fill", "#7CE8D5");

```







               
