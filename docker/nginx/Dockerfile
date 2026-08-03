FROM nginx:alpine

# Özel Nginx Konfigürasyonunu kopyala
COPY custom-jitsi.conf /etc/nginx/conf.d/default.conf

# Statik web içerikleri veya özel temalar için erişim noktası
EXPOSE 80
EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]