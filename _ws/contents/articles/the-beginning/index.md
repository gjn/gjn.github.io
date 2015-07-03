---
title: Hunting down downtimes of map.geo.admin.ch
author: gjn
date: 2015-07-03 20:00
template: article.jade
---

# The phenomenon

It all started with a text message. The team
behind [the Swiss GeoPortal](https://map.geo.admin.ch) and
[its related services](https://api3.geo.admin.ch) recieves
those kind of messages when something is wrong. The message
is sent out by [PingDom](https://pingdom.com), a service
that monitors services and applications on the internet and
reports downtimes.

A single downtime event will get you an warning email by Pingdom.
Getting a text message however means trouble. It's caused by an
incident: a repeated failure from multiple Probes to reach the 
service. Being assertive, we quickly checked the service in question manually.
It turned out to be working just fine and within expected
response times. This was confirmed within minutes by another
PingDom test message declaring the incident over.

For over a year, this pattern repeated itself a couple of times per
month. Incident via text message, manual checks couldn't conclusively confirm
the downtime, text message announcing end of incident. And the incidents
seemed to be randomly distributed among our services. One day, it was
our search service being reported down, the other it was our main
application. Also, th incidents could happen anytime: during lazy morning
hours, peak hours just before lunch or even late at night.

While the analysis of the incidents in rare cases did reveal flaws
in our software stack that we were able to fix quickly, most incidents
remained a mystery to us. Happening randomly, distributed among
all our services, any time of the day.

## Can we trust pingdom?

As most of our incidents could not be directly verified by
hand and were reported over by PingDom in very short time, we
began to suspect troubles with


## Accelerating troubles

# The analysis

## Needle in the hey

## The quick hint

# The fix

# The lessons

## Trust your tools

We should have trusted PingDom. We should have investigated the problem much
earlier under the assumptions that pingdom was, in fact, reporting downtimes
correctly. PingDom didn't report false incidents. If anything, it reported
not enough true incidents. But this was the result of how we set up
our PingDom checks. A few services are checked very minute, most every
5 minutes only. With the mini downtimes caused by Varnish, PingDom was simply
lucky to hit such an event.

## Trust is good, control is better

If you happen to mistrust one of your tools or some piece of software,
test it heavily. Use alternative to test your tools. Ceate custom tests
to validate your tools. Do anything to confirm either your mistrust or the tool.
The worst you can do is remainng in a state of insecurity  Get out of it.

## How organisation impacts your work

## Zero tolerance

Apply a zero tolerance policy for all things in production. Even
the slighest glitch is pointing to a more real, potentially severe problem
that could make our services vurnerable.

Hunt them down mercilessly, until you fully understand their cause. Once
we focused full time on the analysis of the misterious downtimes, we were
able to find and fix the cause within days. Sleep has been
much better since.
