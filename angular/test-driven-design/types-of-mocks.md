# Types of Mocks

## Dummies

Simplest type is dummy. Dummy are object that fill a place.

## Stubs

A stub is an object that has controllable behavior. If we call certain method on a stub we can decide in our test what value that method call will return.

## Spies

A spies is an object that keep track of which of its methods were called, How many time it called and What parameter were used for each call. 

Most of the time these are the object that we use when we need a mock and many time boundaries between these three are blurred.

## True Mock

These are more complex that verify that they were used exactly a specific way. For example, they can check that only specific method were called and that was called only once and have some specific parameter.

