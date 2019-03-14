# Do you have to put every piece of state in the store



No we don’t. What should not go into store are:

* Unshared State
  * That is solely owned by a single component that does not need to be shared or made available across routes.
* Angular form State
  * It is usually self contained and do not need to be shared across multiple component.
* Non-serializable state
  * State that has cycles in it or has complex data structure that cannot be serialized should not be put into the store. For example whole router state should not be put into store because it is not serializable

