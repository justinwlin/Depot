# Depot
Tips on getting started with Depot

## Top Commands:

First one is the **build command**. Where you get started.
```
depot build -t justinwlin/fooocus:1.0 . --platform linux/amd64
```

Second one is you can specify a --platform. This is helpful especially if you are building on Mac. Even though you have BuildX with Docker now,
I think this is more simple and also you get Depot's caching.
```
--platform linux/amd64
```

A great flag to add is the --save command:
https://depot.dev/docs/guides/ephemeral-registry#pushing
```
depot build -t justinwlin/fooocus:1.0 . --platform linux/amd64 --save
```
This will save it to an emphemeral registry on Depot's end. 

From there you can either pull it OR push it directly to docker.
https://depot.dev/docs/guides/ephemeral-registry#pulling
```
depot pull <build-id> -t <image-name>:<tag>
```
Push to docker! (**THIS IS AMAZING** b/c what this means is you do not need to download to your own computer and get bottle-neck by your internet upload speed, rather you are relying on Depot's remote infrastructure)
```
depot push <build-id> -t <image-name>:<tag>
```

# Top Combined Command:
Thus b/c push pushes to a remote infrastructure directly, I like to do the below:
```
depot build -t justinwlin/fooocus:1.0 . --push --platform linux/amd64
```
Or if I want it in an emphemeral registry for testing:
```
depot build -t justinwlin/fooocus:1.0 . --push --platform linux/amd64 --save
```
Or if I don't want to push and only keep it in the empheral registry:
```
depot build -t justinwlin/fooocus:1.0 . --platform linux/amd64
```
