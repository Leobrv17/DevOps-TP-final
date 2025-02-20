# Étape 1 : Construction du projet
FROM node:22-slim AS builder

# Définition du répertoire de travail
WORKDIR /app

# Copie des fichiers package.json et package-lock.json
COPY package.json package-lock.json ./

# Installation des dépendances
RUN npm install

# Copie du reste du code source
COPY . .

# Build du projet
RUN npm run build

# Étape 2 : Serveur Nginx pour la production
FROM nginx:alpine

# Copie du build dans le dossier Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Copie de la configuration Nginx (si nécessaire)
# COPY nginx.conf /etc/nginx/conf.d/default.conf

# Exposition du port 80
EXPOSE 80

# Lancement de Nginx
CMD ["nginx", "-g", "daemon off;"]


