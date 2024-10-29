# Image de build pour la prod
FROM node:23.0.0-alpine AS builder
ENV PORT 3000
WORKDIR /app
COPY . .
RUN npm install --omit=dev --production=true
RUN NODE_ENV=production npm run build && npm prune --production

# Image de prod
FROM node:23.0.0-alpine AS prod
WORKDIR /app
ENV NODE_ENV production
ENV PORT 3000
ENV NEXT_TELEMETRY_DISABLED 1
COPY --from=builder /app/next.config.mjs ./
COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static
CMD ["node", "server.js"]

# Inspiré par :
# https://medium.com/geekculture/optimally-dockerizing-nextjs-application-and-lessons-learned-af1833e7da46
