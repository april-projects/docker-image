FROM openjdk:21-jdk-slim AS java21

# 设置时区
ENV TZ Asia/Shanghai

# 修改APK源为阿里云，安装必要的工具并设置时区
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk update && \
    apk add ttf-dejavu alpine-conf && \
    /sbin/setup-timezone -z Asia/Shanghai && \
    apk del alpine-conf && \
    rm -rf /var/cache/apk/*