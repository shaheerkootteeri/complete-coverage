# complete-coverage

As a sanity check, unit tests should pass, and we can build our program by running the following:

```
go test ./...
go build
```

## Building a binary for coverage profiling
To build an application for collecting coverage profiles, pass the -cover flag when invoking go build on the application binary target.

```
go build -cover -o ./bin/add ./cmd/add
```

## Running a coverage-instrumented binary
Binaries built with “-cover” write out profile data files at the end of their execution to a directory specified via the environment variable GOCOVERDIR.

Start by creating a directory coverage/int for our coverage reports for integration tests.

```
mkdir coverage/integration
```

set the GOCOVERDIR and run the following command:

```
GOCOVERDIR=coverage/integration ./bin/add 1 3
```

we can see code coverage from our integration tests (executing ./bin/add twice) by running:
```
go tool covdata percent -i=./coverage/unit
```
