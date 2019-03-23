# RxJS Operator

## switchMap

It cancels the current subscription/ request and can cause race condition. 

{% hint style="info" %}
Use for get requests or cancelled requests like search.
{% endhint %}

## concatMap

Runs subscription/request in order and is less performant. 

{% hint style="info" %}
Use for get, post and put requests when order is important
{% endhint %}

## mergeMap

Runs subscription/request in parallel

{% hint style="info" %}
Use for put, post and delete methods when order is not important
{% endhint %}

## exhaustMap

Ignores all subsequent subscriptions/requests until it completes

{% hint style="info" %}
Use for login when we do not want more requests until the initial one is completed
{% endhint %}

