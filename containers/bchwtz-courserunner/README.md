# Container Description

## Building the Container

```
docker build -t courserunner .
docker tag <IMAGE ID> ghcr.io/bchwtz/courserunner:latest
```


## Push Container to GHCR

You need to login to GHCR first: 

https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#authenticating-to-the-container-registry


```
docker push ghcr.io/bchwtz/courserunner:latest
```

