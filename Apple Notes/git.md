porcelain
plumbing

git is like a key value store. the key is sha1 now transitioning to sha256. the value is a blob. 

[[IMG_3704.png]]


everything lives inside .git

blobs are stored in objects/ directory

tree in git - stores directory structure

tree is still a blob. but has the identifier 'tree' instead of 'blob'. and points to other trees or blobs. 

identical content will have the same hash. so it's only stored once, and everyone does a reference to it.