# Frontend Dockerfile - React
FROM node:20

WORKDIR /app

# Kopírovanie package.json a package-lock.json
COPY package*.json ./

# Inštalácia závislostí
RUN npm install

# Kopírovanie celého projektu
COPY . .

EXPOSE 3000

CMD ["npm", "start"]
