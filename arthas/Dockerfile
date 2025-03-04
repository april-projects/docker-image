# 使用官方OpenJDK镜像作为基础
FROM openjdk:11-jdk-slim

# 安装必要工具
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# 设置Arthas版本和安装路径
ENV ARTHAS_HOME=/opt/arthas

# 下载并安装Arthas
RUN wget -qO /tmp/arthas.zip "https://arthas.aliyun.com/arthas-boot.jar" && \
    mkdir -p ${ARTHAS_HOME} && \
    unzip /tmp/arthas.zip -d ${ARTHAS_HOME} && \
    rm -f /tmp/arthas.zip

# 创建非root用户
RUN useradd -ms /bin/bash arthas
USER arthas
WORKDIR /home/arthas

# 设置入口点（保持容器运行）
ENTRYPOINT ["sleep", "infinity"]