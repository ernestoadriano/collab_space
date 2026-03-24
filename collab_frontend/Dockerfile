# 1. Estágio de Build (Muito importante a parte "AS build")
FROM node:20-slim AS build
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# 2. Estágio de Execução
FROM node:20-slim
WORKDIR /app
RUN npm install -g serve
# Copia da pasta 'dist' do estágio 'build' para a pasta atual
COPY --from=build /app/dist .

EXPOSE 80
# O ponto (.) indica para servir a pasta atual
CMD ["serve", "-s", ".", "-l", "80"]