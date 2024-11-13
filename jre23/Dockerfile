# 使用 JDK 作为基础镜像
FROM openjdk:23-jdk-slim AS java23

# 设置时区
ENV TZ=Asia/Shanghai

# 修改 APK 源为阿里云并安装必要的工具
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk update && \
    apk add --no-cache ttf-dejavu alpine-conf && \
    /sbin/setup-timezone -z Asia/Shanghai && \
    apk del alpine-conf && \
    rm -rf /var/cache/apk/*

# 删除不需要的开发工具，精简为 JRE
RUN apt-get purge -y \
    build-essential \
    openjdk-23-jdk \
    && rm -rf /var/cache/apt/* /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /usr/lib/jvm/java-23-openjdk

# 设置 JAVA_HOME 环境变量
ENV JAVA_HOME=/usr/lib/jvm/java-23-openjdk
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# 验证 Java 版本
RUN java -version