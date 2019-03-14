# Why use Redux

Without Redux as we build our application we may define some service to define some state or communicate data from one component to another or for better reusable code.

And as we add more feature to our application we create more services with a similar purposes. Over time we may find our self with dozens of services.

With Redux we don’t need a service, rather we have a single store for our application making it easy to find, track and retrive state.

Some of the Benefits are :-

1. Less api calls on page init
2. No need client side cache
3. If something is not working correctly the redux has a tool to debug. We can even rollback and do time travel debugging. It keeps component decoupled and yet communicating
4. It avoids Race condition
5. Performance
   * Easier to make change detection strategy in our component called OnPush and hence improve View performance.
6. Tooling
7. Unit Testing Easier
   * Pure Function

![](../.gitbook/assets/image%20%281%29.png)

