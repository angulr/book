# Migrating to Version 5.x

## Migrate V4 to V5

* Data Loading as Promises
  * The function uses Promise rather then asynchronous callback to load data in.
* Deprecation of d3.queue\(\)
  * We don't need to use queue for loading multiple sets of data
* Removed d3.schemeCatagory20
  * We can use any other color schema like schemeAccent etc.
* Addition of the d3-scale-chromatic module

## Migrate V3 to V4

| V3 | V4 |
| :--- | :--- |
| d3.layout.pie\(\) | d3.pie\(\) |
| d3.layout.force\(\) | d3.force\(\) |
| d3.layout.stack\(\) | d3.stack\(\) |
| d3.layout.treemap\(\) | d3.treemap\(\) |
| d3.scale.time\(\) | d3.scaleTime\(\) |
| d3.scale.linear\(\) | d3.scaleLinear\(\) |
| d3.scale.log\(\) | d3.scaleLog\(\) |
| d3.scale.catagory20\(\) | d3.scaleOrdinal\(d3.schemaCatagory20\(\)\) |



