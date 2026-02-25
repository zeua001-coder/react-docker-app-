# Declaramos nuestra primera etapa (stage) con la parte AS build
FROM node AS build

WORKDIR /app

COPY ./package.json ./

RUN npm install

COPY ./ ./

RUN npm run build

# Inicia nuestra siguiente stage
FROM nginx

# Copiaremos los archivos generados desde la fase build hacia directorio de Nginx
COPY --from=build /app/build /usr/share/nginx/html
