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

## Example Linear Scale

{% embed url="https://jsfiddle.net/niisar/hy90nweb/" %}

## Types of Scales in D3

### scaleLinear

```javascript
var y = d3.scaleLinear()
          .domain([0, 823])
          .range([0, 400]);
          
console.log(y(100))          // 48.3
console.log(y(700))          // 338.2

console.log(y.invert(43.2))   // 100
console.log(y.invert(338.2))  // 700          
```

### scaleLog

```javascript
var x = d3.scaleLog()
          .domain([300, 150000])
          .range([0, 400])
          .base(10);
          
console.log(x(500))           // 32.9
console.log(x(5000))          // 181.1
console.log(x(50000))         // 329.3

console.log(x.invert(32.9))   // 500
console.log(x.invert(181.1))  // 500
console.log(x.invert(329.3))  // 50000
```

### scaleTime

```javascript
var x = d3.scaleTime()
          .domain([new Date(2000, 0, 1), new Date(2001, 0, 1)])
          .range([0, 400]);
          
console.log(x(new Date(2000, 7, 1)))   // 199
console.log(x.invert(232.8))            // Wed Mar 01 2000
```

### scaleOrdinal

```javascript
var color = d3.scaleOrdinal()
              .domain(['Africa', 'N. America', 'Europe', 'S. America', 'Asia', 'Australia'])
              .range(['RED', 'ORANGE', 'YELLOW', 'GREEN', 'BLUE', 'INDIGO', 'GREY'])
              
console.log(color('Africa')) // RED
console.log(color('Asia')) // Blue
```

### scaleBand

```javascript
var x = d3.scaleBand()
          .domain(['Africa', 'N. America', 'Europe', 'S. America', 'Asia', 'Australia'])
          .range([0, 400])
          .paddingInner(0.3)
          .paddingOuter(0.2);
          
console.log(x('S. Anerica'))  // 209
console.log(x('Australia'))   // 341
console.log(x('Africa'))      // 13.1

console.log(x('S. Anerica'))  // 45.9
```

#### Scale Band Example

{% embed url="https://jsfiddle.net/niisar/g59vcdeh/" %}



