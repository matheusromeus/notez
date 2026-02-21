stale-time

next js automatically caches your fetch requests in server components

you add suspense just above where the async data fetching is happening.

rsc payload

- simply await fetch an endpoint, or use prisma to get back data.
- client components: react query, or react's use hook

fetch 'force-cache'
If you are *not* using fetch, and instead using an ORM or database directly, you can wrap your data fetch with the [React cache](https://react.dev/reference/react/cache) function.

when using async await, data will be fetched and rendered on the server for every request. use streaming for that.  


next.config.mjs
env.js

next config, eslint ignoreduringbuild - true, typescript also same thing 

npm run build - preview build, what's gets pushed is prod

get the .yaml file from drive tutorial or picthing

and add a CI to do all this, when pushing to github. 


connection pooling from the frontend - instead of one connection for each user, 

maxidle - is there an equivalent in supabase