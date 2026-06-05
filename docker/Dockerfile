# Build and run the TradeNote app in a single image for Coolify and plain Docker Compose.
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . ./
RUN npm run build

ENV NODE_ENV=production

EXPOSE 8080

CMD ["npm", "start"]