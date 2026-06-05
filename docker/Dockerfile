# Build and run the TradeNote app in a single image for Coolify and plain Docker Compose.
FROM node:18-alpine

RUN apk add --no-cache tzdata

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . ./
RUN npm run build

ENV NODE_ENV=production

EXPOSE 8080

HEALTHCHECK --interval=30s --timeout=10s --retries=3 --start-period=30s \
  CMD wget --no-verbose --spider http://localhost:${TRADENOTE_PORT:-8080}/health || exit 1

CMD ["npm", "start"]