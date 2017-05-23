FROM nginx:1.11
ENV TZ=Asia/Shanghai
COPY  ./conf/nginx.conf /etc/nginx/conf.d/default.conf
CMD ["nginx", "-g", "daemon off;"]

