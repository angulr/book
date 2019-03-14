# Tooltip using d3-tip library

## Step 1: Initializing the tooltip

```javascript
tip = d3.tip().attr('class', 'd3-tip').html(function(d) { return d; });
```

## Step 2: Calling the tip in the context of the visualization

```javascript
vis.call(tip)
```

## Step 3: Adding event listeners

```javascript
vis.selectAll('rect')
  .data(data)
  .enter()
  .append('rect')
  .attr('width', function() { return x.rangeBand() })
  .attr('height', function(d) { return h - y(d) })
  .attr('y', function(d) { return y(d) })
  .attr('x', function(d, i) { return x(i) })
  .on('mouseover', tip.show)
  .on('mouseout', tip.hide)
```

## Example

{% embed url="https://jsfiddle.net/niisar/xmouk9yc/" %}





