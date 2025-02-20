# Utilisation d'une image Node.js de base
FROM node:22-alpine

# Définition du répertoire de travail
WORKDIR /usr/src/app

# Instalation des dépendances nécessaires
RUN apk update && apk add --no-cache openssl

# Copie des fichiers package.json et package-lock.json
COPY package*.json ./

# Installation des dépendances (y compris bcrypt)
RUN npm install -- production

# Copie du reste du code source
COPY . .

# Génération Prisma
RUN npx prisma generate

# Exposition du port
EXPOSE 3000

# Lancement du serveur
CMD ["node", "server.js"]
