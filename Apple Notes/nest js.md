you can create web servers, micro services applications, (both are same but they can use different transport protocols and they can communicate via an internal network), stand-alone apps (no network listener, great for creating scheduled tasks or cli tools) 

but they all need a root module.

modules - they are the building blocks, a nest js app is like a graph of modules and on top you have the root module and that can have modules like a pyramid scheme and use each other

it's a class with the module decorator @Module

decorators - special kind of function, you can add it to anything and it modifies their behaviour and even add metadata

once you have modules you can add controllers in them

controllers -