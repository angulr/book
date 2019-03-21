# Lazy Loading Interface

We must be knowing how to lazy loading of route in our application but how to do or maintain a lazy loading for different class file and interface.

## Non Lazy Loaded Interface, Class

App Component or App Module are the root of our application and if we import a class or interface directly to Root Class then we are breaking the Lazy Loading Principal.

![](../.gitbook/assets/image%20%285%29.png)

## Lazy Loaded Interface Example

We can remove `ProductState` importing directly from app

![](../.gitbook/assets/image%20%288%29.png)

and extend it to Child Component.

![](../.gitbook/assets/image%20%2816%29.png)

This extend is defined to keep our lazy loading boundary intact.

