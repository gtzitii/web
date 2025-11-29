# 使用官方 OpenJDK 21 JDK 镜像
FROM openjdk:latest
# 设置工作目录
WORKDIR /app

# 复制你的 jar 包到容器
COPY demo1.jar app.jar


# 启动命令
ENTRYPOINT ["java","-jar","app.jar"]

