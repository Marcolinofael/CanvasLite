# --- FASE 1: BUILD DO FRONTEND (React) ---
FROM node:18-slim as build

WORKDIR /app

# Copia e instala as dependências do frontend
COPY package*.json ./
RUN npm install

# Copia o código-fonte e executa o build de produção
COPY . .
# Verifica se o script de build no package.json é 'build'
RUN npm run build


# --- FASE 2: SERVIÇO COM NGINX ---
FROM nginx:alpine

# Copia os arquivos estáticos compilados para o Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Copia a configuração personalizada do Nginx (Veja o ponto C abaixo!)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Comando padrão do Nginx
CMD ["nginx", "-g", "daemon off;"]
