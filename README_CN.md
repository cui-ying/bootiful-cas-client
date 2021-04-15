## Bootiful CAS-enabled web application

这是最简单的 CAS 化的 Spring Boot 应用程序。
它使用[official CAS Client](https://github.com/apereo/java-cas-client#spring-boot-autoconfiguration) 。

它可以作为模板来构建更复杂的支持 CAS 的 Spring Boot 应用程序，或者简单地作为各种 CAS 服务器安装的快速测试器。

### 开始吧

* 确保已安装 Java 8 (Java 版本低于 8 将不工作)

* 克隆这个仓库

* 核实 `build.gradle` 文件中的依赖 _`org.jasig.cas.client:cas-client-support-springboot`_ 更新到最新版本。

* 修改 `src/main/resources/application.yml` 中的3处需要的 URL 属性，指向希望的 CAS 服务器和客户端主机。例如：

  ```yaml
  cas:
    #Required properties
    server-url-prefix: https://localhost:8143/cas
    server-login-url: https://localhost:8143/cas/login
    client-host-url: https://localhost:8443
  ```

* 修改 `src/main/resources/application.yml` 中的 SSL 设置，指向你的本地 keystore 和 truststore。例如：
 
 ```yaml
 server:
   port: 8443
   ssl:
     enabled: true
     key-store: /etc/cas/thekeystore
     key-store-password: changeit     
 ```
 
  > 注意: 你也可能需要做自有认证生成/导入 JVM 的 信任库，以让 CAS 客户端/服务器 SSL 握手通信正常工作。

* 从这个命令开始运行 `./gradlew clean bootRun`

* 在浏览器中访问 `https://localhost:8443` ，并享受 CAS 化的 spring boot 应用 ! 
