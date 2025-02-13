# Imagen base mas ligera
FROM nginx:alpine

# Copiar index.html
COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

# Iniciar nginx
CMD ["nginx", "-g", "daemon off;"]