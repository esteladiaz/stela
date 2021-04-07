## Getting started with Serverless

Exciting shift since Components.
- Serverless the Open Source framework
- AWS Serverless
- "Serverless Computing" wikipedia article, etc.

>>> Serverless is other people's servers running your code.

First we all had servers with a **static IP address** that told DNS servers how to find your server with a domain.

A domain doesn't give you a website or webapp. For that you must configure Apache or Nginx, set up a reverse proxy, etc...

### Colocation
A solution for the bedroom problem. What if your power goes out? Residential hosting is not reliable.

>>> Colocation lets you put your server in a data center that gives you rack space, stable power, good internet, and physical security.

You deal with configuration, maintenance, replacing hard drives (as often as every few minutes).

### Virtualization
Colocation solved physical problems, but servers weren't being used to their full potential.
- Usual server runs at 30% utilization, means you're wasting money. The hardware needs to be happy, you need to over-provision in case of traffic spikes or dev mistakes. What if we could run multiple servers on the same machine?

>>> Basic virtual hosts let you run multiple websites on the same machine. A domain maps to an application on your computer, web server knows the mapping, and then sites can share resources.

Problem: you can hack one site and gain access to another. Hack one site, you've hacked them all. Attack one site with lots of traffic, you starve all the others on the same machine of resources. Or if you overlap your configuration, game over.

**Virtual private servers** and **containerization**: rather than multiple websites on the same machine, you can host whole computers on the same machine.

SSH Access providers became popular, pay a bit and you get a live server on the internet with no hardware needed. What if your site gets popular?

### The Cloud
Early VPS was like the cloud, but struggled with scaling. Once traffic grew, you needed more servers to handle th eload. There's only so much a single server can do.

**Vertical scaling**: computers getting stronger and stronger
**Horizontal scaling**: cheaper to share the load between lots of small computers

Problem: how do you ensure all servers are the same, or deal with traffic spikes? By hand.

Set up a server, make sure it works, make a new server, copy config. Repeat.

>>> Cloud servers solve how annoying it is to ensure all servers are the same with automation and containers. Docker for containers, kubernetes for orchestration.

Start every new server from an image in your cloud provider's library. Comes with basic setup and common defaults, add tweaks and make a new image. The cloud provider gives controls to make as many instances of a server as you want. Press a button, get a server.

Cloud servers can scale automatically, detecting rising traffic and creating new servers. When traffic subsides, the same scripts tear the servers down.

### Platform as a Service: PaaS
- Someone else deals with the cloud, you focus on code. They configure servers, dockers, kubernetes, make everything play together. You build the app.

>>> PaaS takes care of servers, you take care of the "frontend" setting up domains, DNS, make your application run right for the platform, configure your own CDN, static files, etc.

### Serverless is born
Once you've got a system that uses containers to scale and descale, uses repeatable configuation, painless deploys, that's serverless!
The main innovation is **tiny containers** and the ecosystem of services and tools around it.

Servers containers are so small you can spin them up and down in ms. They do this bc:

1. Code is small
2. Code is standardized
3. Code does 1 hting

A sevrerless "server" is a function responding to an API endpoint. Request comes in, server wakes up, runs for a bit, goes back down.

The platform takes care of optimization, config, everything. You get an input and return an output.

Severs never idle because they live as long as the request they're serving.

Biggest benefit?

**metered pricing**: no more money wasted on idling servers waiting for requests. Pay for the itme you're getting work done.

