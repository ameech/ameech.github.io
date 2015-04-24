---
published: true
---

## NGINX not streaming when using Puma?

Awhile back we were setting up [Samson](https://github.com/zendesk/samson) at [When I Work](https://wheniwork.com) and we were running into an issue where the deployment logs were not being streamed to the console. After rejiggering a few things in the application, rebooting NGINX and Puma and still not being able to get it to work, we took to Google. After a few minutes of searching we finally found an answer buried on [Stack Overflow](http://stackoverflow.com/a/22429224/941008).

So to save you a few minutes of searching it was as simple as adding this to our NGINX configuration, within the location block:

{% highlight %}
proxy_http_version 1.1;
{% endhighlight %}