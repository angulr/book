# Grant Type

## Client Credentials

No user involved, machine to machine, trusted 1st party sources, server/server

![](../.gitbook/assets/image%20%288%29.png)

## Resource Owner Password

User involved, trusted 1st party apps like SPA, JS, Native 1st Party

![](../.gitbook/assets/image%20%2811%29.png)

## Authorization Code

Google, Facebook, etc, user involved, web app.

## Implicit

It will redirect to Identity Server 4 page and ask for user name and password once credential are entered it will return to callback URL or the client page.  
This flow is best for Web applications, User and Server side web apps

## Hybrid

Combination of implicit and authorization code.

This is best for user, native apps, server side web apps, native desktop, mobile apps

