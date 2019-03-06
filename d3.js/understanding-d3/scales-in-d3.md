# Scales in D3

Scales are functions that map from an input domain to an output range.

```javascript
var y = d3.scaleLinear()
          .domain([0, 823])
          .range([0, 400]);
```

`scaleLinear` construct continuous linear scale where input data \(domain\) maps to specified output range.

```javascript
console.log(y(100))          // 48.3
console.log(y(700))          // 338.2
```

```javascript
console.log(y.invert(43.2))   // 100
console.log(y.invert(338.2))  // 700
```

## Example

{% embed url="https://jsfiddle.net/niisar/hy90nweb/" %}



