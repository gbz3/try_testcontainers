# try_testcontainers

## 初期設定

### Maven

- [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

```
$ mvn -U archetype:generate -DinteractiveMode=false \
    -DarchetypeArtifactId=maven-archetype-quickstart \
    -DarchetypeVersion=1.5 \
    -DgroupId=dev.iamgbz3.tcon \
    -DartifactId=try-testcontainer \
    -Dpackage=dev.iamgbz3.tcon
$ 
```

### Testcontainers

- [Getting started with Testcontainers for Java](https://testcontainers.com/guides/getting-started-with-testcontainers-for-java/)
- [Windows Support](https://java.testcontainers.org/supported_docker_environment/windows/)

#### WSL2 で実行したテストケースが docker 接続に失敗する場合

1. （Windows 側）`Docker Desktop` の `Dashbord` から設定 `Settings > General` で `Expose daemon on tcp://localhost:2375 without TLS` を有効化。
1. （Windows 側）`C:\Users\<YourUsername>\.wslconfig` に以下を設定し、ミラーモードを有効化。
    ```
    [wsl2]
    networkingMode=mirrored
    ```
1. （Windows 側）設定変更を反映するため、WSL2 を停止。
    ```
    > wsl --shutdown
    ```
1. （WSL2 側）環境変数を追加 `export DOCKER_HOST="tcp://localhost:2375"`
