# Stage 1: Build the Vite React App
FROM node:20-alpine AS build

WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve with Vite preview
FROM node:20-alpine AS production

WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/package.json ./
RUN npm install --omit=dev
RUN npm install -g vite

EXPOSE 4173
CMD ["vite", "preview", "--host"]
