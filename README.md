# 本地部署 OverLeaf 完整版

本文档指导你在 Windows 11 上本地部署 OverLeaf 完整版。

## 前提条件
- 安装好 Docker

## 步骤

1. **下载配置文件**
   - 下载 `docker-compose.yml` 和 `compose.override.yaml` 到本地，并放在同一文件夹下。

2. **拉取 Docker 镜像**
   - 在文件夹目录中打开 CMD，输入以下命令拉取[tuetenk0pp
/
sharelatex-full](https://github.com/Tuetenk0pp/sharelatex-full#readme)镜像 ：
     ```bash
     docker pull tuetenk0pp/sharelatex-full
     ```

3. **检查状态**
   - 完成后，输入以下命令查看状态，`sharelatex` 应该是 `restarting` 状态：
     ```bash
     docker ps
     ```

4. **启动 MongoDB**
   - 输入以下命令启动 MongoDB：
     ```bash
     docker-compose up -d mongo
     ```

5. **初始化 MongoDB**
   - 进入 MongoDB 容器并初始化：
     ```bash
     docker exec -it <mongo_container_id> mongo
     rs.initiate()
     exit
     ```

6. **启动 ShareLaTeX**
   - 输入以下命令启动 ShareLaTeX：
     ```bash
     docker-compose up -d
     ```

7. **访问 ShareLaTeX**
   - ShareLaTeX 现在应该是正常状态。打开浏览器访问 [http://localhost/launchpad](http://localhost/launchpad) 进行注册，然后使用 [http://localhost/login](http://localhost/login) 登录。

## 备注
- 使用 `docker ps` 可以查看正在运行的容器。
- 如果需要停止容器，可以使用 `docker stop <容器ID>`。
- 如果需要删除容器，可以使用 `docker rm <容器ID>`。

