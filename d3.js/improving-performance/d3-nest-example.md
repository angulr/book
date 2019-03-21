# D3 Nest Example

## One Level Nest

```javascript
var nested_data = d3.nest()
.key(function(d) { return d.status; })
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%283%29.png)

## Two Level Nest

```javascript
var nested_data = d3.nest()
.key(function(d) { return d.status; })
.key(function(d) { return d.priority; })
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%2821%29.png)

## Rollup to Count and Sum

```javascript
var nested_data = d3.nest()
.key(function(d) { return d.status; })
.key(function(d) { return d.priority; })
.rollup(function(leaves) { 
   return {
      "length": leaves.length, 
      "total_time": d3.sum(leaves, function(d){
        return parseFloat(d.time);
      })
   } 
})
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%281%29.png)

## Rollup to get total of number of lines

```javascript
var nested_data = d3.nest()
.rollup(function(leaves) { return leaves.length; })
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%2823%29.png)

## Sorting

```javascript
var nested_data = d3.nest()
.key(function(d) { return d.status; }).sortKeys(d3.ascending)
.key(function(d) { return d.priority; }).sortKeys(function(d) { return )
.rollup(function(leaves) { return leaves.length; })
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%289%29.png)

## Sorting - custom order

```javascript
var priority_order = ['MUST', "SHOULD", 'COULD', 'WISH'];
var nested_data = d3.nest()
.key(function(d) { return d.status; })
    .sortKeys(d3.ascending)
.key(function(d) { return d.priority; })
    .sortKeys(function(a,b) { 
        return priority_order.indexOf(a) - priority_order.indexOf(b); 
    })
.rollup(function(leaves) { return leaves.length; })
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%2815%29.png)

## Sorting - sort the leaves as well

```javascript
var priority_order = ['MUST', "SHOULD", 'COULD', 'WISH'];
var nested_data = d3.nest()
.key(function(d) { return d.status; })
    .sortKeys(d3.ascending)
.key(function(d) { return d.priority; })
    .sortKeys(function(a,b) { 
        return priority_order.indexOf(a) - priority_order.indexOf(b); 
    })
.sortValues(function(a,b) { 
    return parseFloat(a.time) - parseFloat(b.time); 
} 
.entries(csv_data);
```

![](../../.gitbook/assets/image%20%2814%29.png)

