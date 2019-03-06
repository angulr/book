# Min, Max, Extent and Map function

```javascript
var data = [
    { grade: 'A', value: 4 },
    { grade: 'B', value: 3 },
    { grade: 'C', value: 2 }
]
```

## Min

```javascript
var min = d3.min(data, function(d){
    return d.value
}); // 2
```

## Max

```javascript
var max = d3.max(data, function(d){
    return d.value
}); // 4
```

## Extent

```javascript
var extent = d3.extent(data, function(d){
    return d.value
}); // [2, 4]
```

## Map

```javascript
var map = data.map(data, function(d){
    return d.grade
}); // ['A', 'B', 'C']
```

## Example

{% embed url="https://jsfiddle.net/niisar/rfxmtpk5/" %}





