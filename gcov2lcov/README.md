gcov2lcov converts golang test coverage to lcov format (which can for example be uploaded to coveralls).

This dockerfile patches the original gcov2lov (github.com/jandelgado/gcov2lcov) to avoid asking for modules.

To build the container's image.

```
docker build . -t icsforth/gcov2lcov
```

To upload it to Docker Hub

```
docker push icsforth/gcov2lcov
```
