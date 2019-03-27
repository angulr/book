# Why OAuth Have Both Access Tokens and Refresh Token

OAuth 2.0 protocol has an authorization server that can return both an **access\_token** \(which is used to authenticate oneself with a resource\) as well as a **refresh\_token** \(which is used purely to create a new access\_token\).

**Why do we have both? Why not just make the access\_token last as long as the refresh\_token and not have a refresh\_token! isn't it?**

That actually reason to use Refresh Token is do with claims. Each token contains claims which can include anything like roles or claims. As a token is refreshed these claims are updated. If we refresh the tokens more often then we are getting more accurate and up-to-date claims.

