# Preface: Who Is This Guide For?

## Who is This Guide For?

This is a beginner-to-intermediate level guide intended to help modernize legacy CF deployments or facilitate good habits for new deployments. It might be for you if:

* You manage or maintain Coldfusion applications \(or you want to\)
* You don't have a dedicated DevOps team that knows all of this already
* You've heard of containers and perhaps Docker but you don't know a lot about them and what they can do for you
* You want to modernize your infrastructure and you aren't sure where to begin

The guide assumes an intermediate level of familiarity with Coldfusion and server administration, but even if you're a beginner, we'll always try to provide links to guides for topics we will mention but not cover in depth.

## Why This Guide? or: Stop Adopting Pets

One of the larger investments of time and resources at our company has always been our service infrastructure model, which persisted as a bunch of servers in a data center for over ten years even as AWS and other cloud solutions became the standard. We liked our hosting company; they'd always given us a good deal and we even looked forward to naming new ones every so often. We're also a small company and for us to invest in new architecture might take half or three quarters of our manpower away from development.

At the [Coldfusion Summit](https://twitter.com/hashtag/CFSummit2017?src=hash) in November of 2017, at the end of a presentation given by Luis Majano \([@lmajano](https://twitter.com/lmajano)\) at [Ortus Solutions](https://www.ortussolutions.com/) on an unrelated subject, he had a few minutes left and decided to containerize and deploy the demo application he'd written. He did so with time to spare, and we realized that we were past due in adopting this deployment strategy for our own applications. It wasn't that what we had suddenly became insufficient; rather, it became so easy to "do it right" that maintaining our old infrastructure would have been a larger and more restrictive investment than starting from scratch. It was time to retire the pets and hire some cattle.

A previous presentation had included the below slide, originally from [@randybias](https://www.slideshare.net/randybias/the-cloud-revolution-cyber-press-forum-philippines) at Cloudscaling:

![](.gitbook/assets/servers_pets_or_cattle.jpg)

### Steal What Works

We began by looking for existing resources on cloud Coldfusion deployments. We attended no fewer than four sessions on the subject at CF Summit and found a range of strategies; some were appealing and others had time-consuming shortcomings. All of them assumed you already had cloud architecture provisioned and focused primarily on getting Coldfusion into container form. We wanted to use the opportunity to re-think our entire workflow, using best practices from the CF community.

The foundation for this effort was the excellent [Docker Roadshow](https://www.ortussolutions.com/events/container-roadshow-2017) hosted by Ortus in September of 2017. Their work is the basis for this guide \(along with indispensable utilities like [Commandbox](https://www.ortussolutions.com/products/commandbox) and [CFConfig](https://www.forgebox.io/view/commandbox-cfconfig)\). See Credits & Acknowledgments for the full list!

## Why "End to End?"

About forty miles west of Austin, Texas, there is a [bourbon distillery](http://www.garrisonbros.com/) where nearly the entire process takes place on the premises: they mix the mash, distill it, barrel it, age it, and finally bottle it all right there. Being able to see how everything works together makes it easier to understand every component, particularly if you go in not knowing anything about bourbon. That's what we're trying to accomplish with this guide: provide enough detail so that you can reproduce and use the strategies we like while maintaining a sense of perspective on where each stage fits in the big picture.

There is already a great deal of information about Docker and Coldfusion on the 'net, and Adobe is working on an "official" CF Docker image. This guide borrows liberally from existing work \(with attribution\) but we don't have any religion about our choices: when possible, we've provided alternatives to our choices, and we're happy to hear from you if you think we've missed something.

## Why "In a Week?"

One of the barriers to adopting modern, best-practices hosting solutions is that many of us have already made investments in reliable, battle-tested \(if outdated\) infrastructure such that the notion of throwing it all out and starting over is prohibitive.

One of the goals of this guide is to demonstrate that this is a problem of mindset rather than resources. Many sections of the guide can be consumed in under an hour, and the major themes \(e.g. a complete development environment\) in under a day; you can go "end to end" \(development to production\) in about a week. The individual steps don't require advanced training or expertise.

## What You'll Have When You're Finished

* A development environment you can use on Windows, MacOS, or Linux, and easily replicate for others
* A blueprint for a complete production pipeline in the cloud: database, front-end web server, source repository, container registry, and Docker Swarm
* Cloud computing instances at one of several competing infrastructure providers to support the above
* Your own Docker images for CF development and production
* An understanding of how to scale your infrastructure when the need arises, both vertically \(feeding CF through embiggening your compute instances\) and horizontally \(Distributed CF development, Docker Swarm, and Distributed Caching\)

