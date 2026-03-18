# 软件工程：第11讲：容器化技术 🐳

![](img/1a42bb13f1f61dc00678fe296b0100f6_1.png)

在本节课中，我们将要学习容器化技术。这是一种将应用程序及其所有依赖项打包成一个独立、可移植单元的方法。我们将探讨其核心概念、优势、与虚拟机的区别，并重点学习如何使用 Docker 这一流行的容器化工具。

## 容器化概述

容器化是一种将应用程序的所有依赖项、库和环境变量打包到一个独立可执行文件中的技术。

例如，假设一个人使用 Python 编程，而另一个人只使用 Java。Java 需要 JDK 环境。通过容器化，可以将 Java 代码打包到一个容器中。这样，使用 Python 的人无需安装任何 JDK 或配置环境，就能在自己的机器上运行这个 Java 代码。

容器非常轻量。

## 容器的优势

以下是容器化技术的一些主要优势：

*   **隔离性**：由于所有内容都捆绑在一个独立的容器中，它不需要与容器外的任何东西交互。
*   **一致性**：如果容器在我的机器上能运行，那么它在任何其他机器上也能运行。这意味着，我可以将应用程序所需的一切打包到一个“小盒子”里，然后分发到所有需要的机器上。
*   **高效性**：容器占用的空间更少，因此效率更高。

## 容器的应用场景

容器化技术有多种用途。

*   **微服务架构 vs 单体架构**：容器主要用于微服务架构，但这种架构成本更高。微服务由许多相互交互的容器组成。这与单体架构不同，单体架构使用一个大型服务器来处理所有事情。对于初创公司来说，单体架构成本低廉，这是一个优势。
*   **持续集成与持续部署**：CI/CD 流水线本质上就是一系列相互交互的容器。
*   **易于部署**：容器非常轻量，部署起来不费力。
*   **安全性**：每个容器都是独立且封闭的。如果一个容器出现问题，可以轻松地用另一个相同的容器替换它。这在大型团队设置中更容易处理，因为如果有一百多个容器中的一个出问题，替换起来很简单。而单体架构则需要查看数千行日志来定位问题。可以将单体架构比作只有一个厨房的餐厅，如果厨房着火，整个餐厅都必须关闭。

## 单体架构 vs 微服务架构

如上所述，单体架构非常简单，它有一个数据库来控制一切，成本低廉。

而微服务架构由许多微服务组成，每个微服务可以看作一个容器。一个微服务只处理一个特定的功能或任务，非常模块化。它通常有多个不同的数据库进行交互。

## 虚拟机 vs 容器

虚拟机和容器有所不同。

虚拟机非常占用资源。例如，如果你在 Mac 上尝试运行 Windows 程序，就像在一个操作系统上再运行另一个操作系统。这会消耗大量内存，运行速度非常慢。

容器则很轻量，它不需要另一个操作系统来运行，而是直接与内核协作。内核是连接硬件和软件的桥梁，非常轻量。容器所需的一切都包含在自身内部。

简单来说，虚拟机通过**管理程序**与硬件交互，而容器通过**容器引擎**与内核交互。管理程序本质上是一个托管操作系统的数据库。

## Docker 简介

Docker 是用于在容器中开发、交付和运行应用程序的平台。

简化来说，它是一个基于云的服务，你可以将代码打包并上传到云端。如果你的朋友想获取你的代码，他可以从 Docker 拉取。Docker 本质上是一个容器化系统。

![](img/1a42bb13f1f61dc00678fe296b0100f6_3.png)

需要了解的是，Docker 需要**镜像**。镜像是容器内代码运行方式的蓝图，就像一份食谱说明书。这个镜像将在容器中运行代码。

![](img/1a42bb13f1f61dc00678fe296b0100f6_5.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_7.png)

## 容器编排

![](img/1a42bb13f1f61dc00678fe296b0100f6_9.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_11.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_13.png)

当你构建微服务架构时，规模会迅速扩大。同时处理上百个容器可能不可行，因此需要找到方法来自动化某些操作，例如更新或部署容器。

这就是**容器编排**的用武之地。有一些工具可以实现这一点，例如 Kubernetes。这些工具帮助自动化容器的部署和删除。例如，如果你的服务用户达到上限，你需要部署更多容器来容纳更多用户，就可以通过容器编排来自动化此过程。

此外还有**自愈**功能。当出现故障的容器或微服务时，Kubernetes 等程序会自动丢弃故障容器并放入一个新的。

**更新和回滚**涉及 CI/CD。例如，如果你在本地计算机上开发服务更新，可以将更新推送到云端，系统会自动替换过时的容器并放入新的。

有一些容器编排工具，Kubernetes 可能是最著名的一个。AWS 也提供一系列服务，例如 Fargate 可以自动化容器并处理 CI/CD 流水线；AWS Lambda 是事件驱动编程，意味着它会根据环境变化做出反应，例如网站访问量增加时自动部署更多容器。

AWS 的 Elastic Container Service 基本上是 Amazon 版本的 Docker。还有一些其他服务也处理容器。

![](img/1a42bb13f1f61dc00678fe296b0100f6_15.png)

## Docker 实践入门

Docker 允许你在松散隔离的容器中打包和运行应用程序，让你可以像管理应用程序一样管理基础设施。

### Docker 工作原理

Docker 采用客户端-服务器架构。Docker 客户端与 Docker 守护进程交互。

Docker 守护进程是管理所有 Docker 对象的引擎，包括镜像、容器、网络和卷。Docker 客户端是命令行界面，我们通过它传递要执行的命令。这两个组件都安装在你的主机上。但在某些情况下，你需要将 Docker 客户端连接到服务器上的远程守护进程。

![](img/1a42bb13f1f61dc00678fe296b0100f6_17.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_19.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_21.png)

### Docker 注册表

Docker 注册表是我们存放镜像以便他人拉取的地方。默认的是 Docker Hub，你可以在这里找到任何你想要的镜像。镜像被组织在仓库中。如果你想推送一个镜像，首先需要为该镜像创建一个仓库。还有其他注册表，例如 Amazon Elastic Container Registry 和 Google Container Registry。

### Docker Desktop

Docker Desktop 易于安装，是一个适用于任何计算机的简单应用程序。它允许你管理所有镜像、卷和容器。它包含了 Docker 守护进程、Docker 客户端和 Docker Compose。

### Docker 镜像

Docker 镜像是一个模板或配方，用于配置你想要运行的容器。它包含运行容器所需的所有文件、环境变量、二进制文件和库。我们使用 Dockerfile 来构建镜像。

镜像有两个重要原则：
1.  **不可变性**：一旦创建镜像，就不允许修改它，必须重新创建。
2.  **分层结构**：镜像由多个层组成，每一层都是对前一层的修改，层层叠加。最后一层是可写的。

![](img/1a42bb13f1f61dc00678fe296b0100f6_23.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_25.png)

### Dockerfile 基础

每个 Dockerfile 都必须以基础镜像开始。我们也可以指定版本。指令通常使用大写，这是一种约定，有助于其他开发者理解代码。

![](img/1a42bb13f1f61dc00678fe296b0100f6_27.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_29.png)

以下是一些常见指令：
*   `FROM`：指定基础镜像。
*   `RUN`：执行命令来创建镜像层。
*   `ENV`：设置环境变量。
*   `WORKDIR`：设置工作目录，后续命令将在此目录下执行。
*   `EXPOSE`：暴露端口，以便容器与外部世界交互。
*   `ARG`：定义构建时可覆盖的参数。

![](img/1a42bb13f1f61dc00678fe296b0100f6_31.png)

有两种方式指定容器启动时运行的命令：
*   `CMD`：易于覆盖，只需在运行容器时传递参数即可。
*   `ENTRYPOINT`：难以覆盖，适用于容器总是以相同命令启动的情况。

![](img/1a42bb13f1f61dc00678fe296b0100f6_33.png)

### Docker 容器

容器是一个运行你的应用程序的隔离进程。我们可以创建、启动或删除容器。

![](img/1a42bb13f1f61dc00678fe296b0100f6_35.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_36.png)

Docker 的一个关键特性是，当容器被移除时，数据不会保存，因此你需要使用持久化存储，例如卷。

![](img/1a42bb13f1f61dc00678fe296b0100f6_38.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_39.png)

容器的生命周期包括：创建容器（或直接运行容器）、暂停容器、停止容器和删除容器。

![](img/1a42bb13f1f61dc00678fe296b0100f6_41.png)

### 实践：创建镜像和运行容器

我们将创建一个简单的 Web 应用程序，它从用户获取输入，并在 8080 端口运行。我们需要将容器的端口映射到本地机器的端口。

首先，我们需要一个 Dockerfile。它必须以基础镜像开始，这里我们使用 Python 3。最佳实践是先安装所有依赖项，然后再复制应用程序代码。

以下是一个示例 Dockerfile：
```dockerfile
FROM python:3
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8080
CMD ["python", "app.py"]
```

要构建镜像，在 Dockerfile 所在目录下运行：
```bash
docker build -t my-image .
```
`-t` 选项用于给镜像命名。

要查看镜像列表，运行：
```bash
docker images
```

要使用此镜像创建并运行容器，并进行端口映射，运行：
```bash
docker run -p 8080:8080 my-image
```
第一个端口是主机端口，第二个端口是容器端口。

![](img/1a42bb13f1f61dc00678fe296b0100f6_43.png)

要停止容器，首先需要找到容器名称或 ID：
```bash
docker ps
```
然后使用名称或 ID 停止它：
```bash
docker stop <container_name_or_id>
```

要删除容器，运行：
```bash
docker rm <container_name_or_id>
```
使用 `docker ps -a` 可以列出所有容器（包括已停止的）。

`docker run` 命令会直接创建并运行容器。如果只想创建容器而不运行，可以使用 `docker create` 命令。`--rm` 标志可以在容器退出后自动删除它。如果不指定名称，Docker 会随机生成一个。

### 与容器交互

![](img/1a42bb13f1f61dc00678fe296b0100f6_45.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_47.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_49.png)

如果以后台模式运行容器，你可以将其附加到命令行以查看日志：
```bash
docker attach <container_name>
```
或者使用 `docker logs` 命令查看日志。

![](img/1a42bb13f1f61dc00678fe296b0100f6_51.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_53.png)

### 推送镜像到注册表

要将镜像推送到 Docker Hub，首先需要在 Docker Hub 上创建一个仓库。然后，你需要给本地镜像打上标签，标签名应与你的仓库名匹配（格式为 `用户名/仓库名`）。

![](img/1a42bb13f1f61dc00678fe296b0100f6_55.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_57.png)

```bash
docker tag my-image username/repo-name:tag
```
然后登录 Docker Hub：
```bash
docker login
```
最后推送镜像：
```bash
docker push username/repo-name:tag
```
如果忘记指定标签，默认会使用 `latest` 标签。

![](img/1a42bb13f1f61dc00678fe296b0100f6_59.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_61.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_63.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_64.png)

## Docker Compose 简介

Docker Compose 用于在同一个主机上运行多容器应用程序环境。它比 Kubernetes 简单，适用于小规模场景。

![](img/1a42bb13f1f61dc00678fe296b0100f6_66.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_68.png)

Docker Compose 是一个运行多容器应用程序的工具。我们使用一个 YAML 格式的配置文件，通常命名为 `docker-compose.yml`。

Compose 文件有不同的配置层级：
*   **服务**：定义容器的抽象配置。
*   **网络**：定义容器之间通信的空间。
*   **卷**：定义持久化数据存储。
*   **配置**：用于运行时或平台的配置。
*   **密钥**：用于敏感数据的特定配置。

我们将主要关注服务层级。

![](img/1a42bb13f1f61dc00678fe296b0100f6_70.png)

在服务层级，你可以指定：
*   `build`：指定 Dockerfile 的路径。
*   `container_name`：给容器命名。
*   `depends_on`：控制服务启动顺序。
*   `environment`：设置环境变量。
*   `image`：指定使用的镜像。
*   `networks`：指定容器加入的网络。
*   `ports`：进行端口映射。
*   `restart`：定义重启策略（如 `always`, `no`）。

![](img/1a42bb13f1f61dc00678fe296b0100f6_72.png)

常用的 Docker Compose 命令包括：
*   `docker-compose up`：启动所有服务。
*   `docker-compose down`：停止并移除所有服务。
*   `docker-compose logs`：查看服务日志。
*   `docker-compose ps`：列出服务状态。

![](img/1a42bb13f1f61dc00678fe296b0100f6_73.png)

### 实践：使用 Docker Compose

我们将创建一个包含应用程序和数据库（MySQL）的简单 Web 应用。应用程序将用户输入保存到数据库中。

`docker-compose.yml` 文件示例：
```yaml
version: '3.8'
services:
  app:
    build: .
    depends_on:
      - db
    restart: always
    ports:
      - "8080:8080"
    networks:
      - my-network
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: mydb
    networks:
      - my-network
networks:
  my-network:
```

![](img/1a42bb13f1f61dc00678fe296b0100f6_75.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_77.png)

在包含此文件的目录下运行：
```bash
docker-compose up
```
这将启动应用和数据库服务。由于应用启动时数据库可能尚未完全就绪，我们配置了 `restart: always` 让应用不断重试。

![](img/1a42bb13f1f61dc00678fe296b0100f6_79.png)

![](img/1a42bb13f1f61dc00678fe296b0100f6_81.png)

要检查数据库中的数据，我们可以运行一个 MySQL 客户端容器连接到同一个网络：
```bash
docker run -it --rm --network=compose-demo_my-network mysql:5.7 mysql -h db -u root -p
```
然后输入密码并查询数据。

## 总结

![](img/1a42bb13f1f61dc00678fe296b0100f6_83.png)

本节课中，我们一起学习了容器化技术。我们了解了容器如何通过打包所有依赖项来实现环境一致性和隔离性，比较了容器与虚拟机的区别，并深入探讨了 Docker 这一核心工具。我们学习了 Docker 镜像和容器的概念，实践了如何构建镜像、运行容器以及使用 Docker Compose 管理多服务应用。这些知识为在现代软件工程中构建可移植、可扩展的应用程序奠定了基础。