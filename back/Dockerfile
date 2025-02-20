# Utilisation d'une image Node.js de base
FROM node:22-slim

# Définition du répertoire de travail
WORKDIR /app

# Instalation des dépendances nécessaires
RUN apt-get update -y && apt-get install -y openssl python3 make g++

# Copie des fichiers package.json et package-lock.json
COPY package.json package-lock.json ./

# Installation des dépendances (y compris bcrypt)
RUN npm install

# Copie du reste du code source
COPY . .

# Génération Prisma
RUN npx prisma generate

# Migration des tables
RUN npx prisma migrate dev

# Exposition du port
EXPOSE 3000

# Lancement du serveur
CMD ["node", "server.js"]
