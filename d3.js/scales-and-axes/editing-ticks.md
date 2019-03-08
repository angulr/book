# Editing ticks

## How many ?

```javascript
d3.axisBottom(x)
  .ticks(10)
```

## Text format

```javascript
d3.axisBottom(x)
  .tickFormat(d3.format(', .0f'));
  
// Custom formatting
d3.axisBottom(x)
  .tickFormat((d) => {
     return *TICK TEXT*
  });
```

## Explicit values

```javascript
d3.axisBottom(x)
  .tickValues([1, 2, 3, 4, 5, 8, 13, 21])
```





