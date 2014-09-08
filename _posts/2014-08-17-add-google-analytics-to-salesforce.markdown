---
layout: post
title: Add Google Analytics to Salesforce
category: posts
---

This solution relies heavily on the ["embed javascript via custom home page sidebar component"](http://salesforce.stackexchange.com/questions/38918/end-of-javascript-sidebar-hacks) design by [Uwe Heim](http://salesforce.stackexchange.com/users/9937/uwe-heim). It’s very easy to put together and best of all, it works!

Setup time approximately **10-15 minutes**.

## Create Google Analytics Account (FREE)

1) Sign-up for your free account at [http://www.google.com/analytics/](http://www.google.com/analytics/)

>You will either need to sign-in with existing Google profile or create a new one. I created a new Google profile just for this purpose to not muck with my personal email account.

>This was my first foray into Google Analytics and took me a minute to understand how to set it up. Right or wrong, I named my “Account” as my company then created two (2) “Properties”, one for my production salesforce org and one for my sandbox org. This way I could keep clicks in the sandbox environment separate from the real site.

2) Create a new **Property** to generate a tracking id. You will need to specify a `Name` and `URL` for the property. Make sure when specifying the URL you use `https://` protocol. The URL should be the base domain you use to log into Salesforce (e.g. `https://<yourdomain>.my.salesforce.com` or `https://<yourserver>.salesforce.com`)

> As noted above, I actually created two properties, one named “Salesforce Production” and the other “Salesforce Sandbox”.

3) As personal preference, if you scroll down on that same **Property Settings** page then under the **In-Page Analytics** section you can enable the [Use enhanced link attribution](https://support.google.com/analytics/answer/2558867?hl=en&utm_id=ad). Because of this, you’ll notice some extra javascript I had to include when we move on to the next step of creating the static resource for Salesforce.

4) And because Salesforce loads standard content and visualforce content on different sub-domains, I also enabled [cross-domain tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/cross-domain), which is a couple more lines of javascript we’ll see in the next step.

![Property Settings]({{ site.github.owner_url }}/blob/master/images/google-analytics/0_analytics.png)

---