
**Platform engineering** is the discipline of building and operating an internal developer platform (IDP) that enables software teams to ship, run, and scale software without managing underlying infrastructure complexity.

Backstage is an IDP. 

The gist is that, Instead of every team manually handling:
- cloud infrastructure
- CI/CD pipelines
- Kubernetes complexity
- observability setup
- security policies
- deployment standards
a **platform engineering team** builds a platform that abstracts these concerns.

(kind of like commands that can run infra automation under the hood)


	Do we have a standard setup that can help us achieve this?
	Are we mature enough to let devs handle infra?


But we can have our own version of this. Like an internal platform. Which would consolidate everything that we do, powered by Roam. Internal blogs written by members, Documentation, any news or things that need to be known. 


So here is how Spotify Backstage is different. It's standardising the entire process of creating anything. Not just infra. It could be infra, but it also can be UI components, a new service, a website, a lambda function (bit lower level this would also be abstracted) etc. 

They are able to do this and its easy for them to standardise because it's just one app. And most people are working on stuff which is part of the main app. So the design language and code structures are already decided. And their ecosystem is also matured. 

some ideas
- A template for starting a new project (according to backend languages and architecture)
- Every team would have their own templates
- PMs can start a documentation template



Auth is via Github
