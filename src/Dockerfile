# Usar una imagen base liviana
FROM node:20.10.0-alpine3.18

# Configurar el entorno
ENV NODE_ENV=production

# Crear un directorio de trabajo
WORKDIR /app

# Copiar solo archivos esenciales para instalar dependencias
COPY package*.json ./

# Instalar dependencias de producción
RUN npm install --only=production && \
    npm cache clean --force

# Copiar el resto de la aplicación
COPY . .

# Configurar permisos y crear un usuario no root
RUN addgroup -S devops_group && adduser -S devops_user -G devops_group && \
    chown -R devops_user:devops_group /app

USER devops_user

# Exponer el puerto de la aplicación
EXPOSE 8080

# Definir el comando de inicio
CMD ["node", "server.js"]

