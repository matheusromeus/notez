caching in browser
disk based cache is faster than a network request 

a traditional database could be running as separate processes which would require IPC or different in different servers

sqlite runs on the same server as a single process with the server. (application code + db sqlite is one process)


theyve used sqlite instead of localstorage.
why not indexeddb

storage limit is a problem

in the browser, js is single threaded hence writing to localstorage is a blocking method

we can run sqlite on a separate thread. using web workers.

applications with need for high availability or speed is a huge criteria where one of the api endpoints can be slow, we can race two requests. 

if they have multiple tabs and data corruption is a problem, send all the requests from all tabs to a shared worker and that directs the request to the active tab worker