FROM node:lts-alpine

WORKDIR /usr/src/app

# Copiar apenas package.json primeiro (para cache)
COPY package*.json ./

# Instalar dependências globais necessárias
RUN npm install

# Copiar o resto
COPY . .

# Expor porta
EXPOSE 5173

# Comando que instala dependências se necessário e roda
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]