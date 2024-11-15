# 使用官方的 OpenJDK 11 Alpine 基础镜像
FROM eclipse-temurin:11-jre-alpine AS java11

# 设置时区为 Asia/Shanghai
RUN apk add --no-cache tzdata \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata

# 删除不必要的文件以减小镜像体积
RUN rm -rf /var/cache/apk/* /usr/lib/lib*.a /usr/share/man \
    && find /usr/lib/jvm -name "*.zip" -exec rm -f {} \; \
    && find /usr/lib/jvm -name "src.zip" -exec rm -f {} \;