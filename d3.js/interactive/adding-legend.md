# Adding Legend

```javascript
var continents = ['europe', 'asia', 'americas', 'africa']

var legend = g.append('g')
   .attr('transform', 'translate(' + (width - 10) +',' + (height - 125) + ')')

continents.forEach((continent, i) => {
  var legendRow = legend.append('g')
    .attr('transform', 'translate(0, ' + (i * 20) + ')');

  legendRow.append('rect')
    .attr('width', 10)
    .attr('height', 10)
    .attr('fill', continentColor(continent))

  legendRow.append('text')
    .attr('x', -10)
    .attr('y', 10)
    .attr('text-anchor', 'end')
    .style('text-transform', 'capitalize')
    .text(continent)
});
```

## Example 

{% embed url="https://jsfiddle.net/niisar/1ctybwdL/" %}



