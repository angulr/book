# Axis Generators

## Left

```javascript
var leftAxis = d3.axisLeft('Y SCALE');
g.append('g')
 .attr('class', 'left axis')
 .call(leftAxis)
```

## Top

```javascript
var topAxis = d3.axisTop('X SCALE');
g.append('g')
 .attr('class', 'top axis')
 .call(topAxis)
```

## Bottom

```javascript
var bottomAxis = d3.axisBottom('X SCALE');
g.append('g')
 .attr('class', 'bottom axis')
 .attr('transform', 'translate(0,' + height + ')')
 .call(bottomAxis)
```

## Right

```javascript
var rightAxis = d3.axisRight('Y SCALE');
g.append('g')
 .attr('class', 'right-axis')
 .attr('transform', 'translate(0,' + width + ')')
 .call(rightAxis)
```

