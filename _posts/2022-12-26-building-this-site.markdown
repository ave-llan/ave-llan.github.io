---
layout: post
title:  "How this site works"
date:   2022-12-26
categories: writing tech
---
This site is built with [Jekyll](https://jekyllrb.com/). The simple source code is available on [Github](https://github.com/ave-llan/ave-llan.github.io). 

I wanted a simple workflow to publish changes, and have been able to achieve that with a Cloud Build trigger that watches my Github repository for changes. Whenever I push a change to github, the change is live on this page in about a minute. 


# Hosting with Google Cloud
I followed this [guide](https://cloud.google.com/storage/docs/hosting-static-website) to host it via a Google Cloud Storage bucket, and set up a trigger in Cloud Build to update it whenever I push a change to Github (this [tutorial](http://notes.nestorlafon.com/tech/2020/12/29/jekyll-site-ci-cd-in-gcp.html) was helpful).

I'm quite happy with the workflow but there are a few downsides. Google Cloud offers many [free tiers](https://cloud.google.com/free) and for small sites like this it should be easy to stay below the [free usage limits](https://cloud.google.com/free/docs/free-cloud-features#free-tier-usage-limits).  

However, the [hosting a static website guide](https://cloud.google.com/storage/docs/hosting-static-website) that Google Cloud provides has you [set up a load balancer](https://cloud.google.com/storage/docs/hosting-static-website#lb-ssl) which is not part of any free tiers. I was chared $0.54 for the first full day of running it. Because of this I am looking into switching to App Engine.

Another small downside: required page file extensions (`.html`) because there isn't much room for custom serving logic.

