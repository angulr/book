# State, Action, Reducer

## What is State

State can be View State, User Information, Entity Data, User Selection and Input. Hear purpose of Redux is to Organise state in to one local single state container.

## What is Action



![](https://lh5.googleusercontent.com/jbby4SKeXgrpRpEetieQWMKYnhPXFS-lQ6ZzdvFijRN2MKmNSdxKSoQ7qpjJ7xF4Qz7xj44pkrH9j02K5J6AjM8uaJnNLc0ilpdXjzFYptz0qriyq0iJwSRs979ENktpj2dXItbY)

Action are simple JavaScript object with a type as a string and an optional payload that can of any type.

## What is Reducer

![](https://lh3.googleusercontent.com/PgFFPkBdweXG_a7Z6JbGMobfx1HjIlR4g9FFTYIPETTlC6VLmPoJsL6AGbPj9rCBzaZK2WbBocVfimRn_k2irz-IlWK_8NnAtjftW7dBAZVltP5Jqkz1jLEGMZJ9dL7OcKyB3f83)

A reducer is a pure function, accepting two arguments. The previous state and action that dispatch the update state. Reducer uses switch statements to listen and act on specific action types, taking the actions payload and state and returning the new state.



