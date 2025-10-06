# Usa uma imagem base oficial do Node
FROM node:18-slim AS base

# Define o diretório de trabalho
WORKDIR /usr/src/app

# Copia e instala as dependências do backend
COPY package*.json ./
RUN npm install

# Copia o restante do código da API
COPY . .

# Expõe a porta definida no docker-compose.yml
EXPOSE 5000

# Comando para iniciar o servidor Express (deve ser o 'start' no package.json)
CMD [ "npm", "start" ]
