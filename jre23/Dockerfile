# 基于 Eclipse Temurin 提供的 JRE 23 Alpine 基础镜像
FROM eclipse-temurin:23-jre-alpine

# 设置时区为 Asia/Shanghai
RUN apk add --no-cache tzdata \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata

# 删除不必要的文件以减小镜像体积
RUN rm -rf /var/cache/apk/* /usr/lib/lib*.a /usr/share/man \
    && find /opt/java/openjdk -name "*.zip" -exec rm -f {} \; \
    && find /opt/java/openjdk -name "src.zip" -exec rm -f {} \;