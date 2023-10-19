# gax-httpjson-streaming-test-repro
Replicating project in https://github.com/googleapis/sdk-platform-java/issues/1193 created by @suztomo.

1. Run the following command to create copy over http-json code from sdk-platform-java/gax:
```
rm -rf gax-test00/src/test;cp -r ~/IdeaProjects/sdk-platform-java/gax-java/gax-httpjson/src/test ./gax-test00/src/test; cp ~/IdeaProjects/sdk-platform-java/gax-java/gax-httpjson/src/main/java/com/google/api/gax/httpjson/HttpJsonDirectServerStreamingCallable.java gax-test00/src/test/java/com/google/api/gax/httpjson; mkdir gax-test00/src/test/java/com/google/api/gax/; cp -r ~/IdeaProjects/sdk-platform-java/gax-java/gax/src/test/java/com/google/api/gax/rpc gax-test00/src/test/java/com/google/api
```

2. Run this command to replicate modules
```
sh replicate_module.sh
```
3. Command to run test concurrency:
```
mvn test --errors --no-transfer-progress -Dcheckstyle.skip -T 2C -Dtest='HttpJsonDirectServerStreamingCallableTest#testManualFlowControl*'
```
