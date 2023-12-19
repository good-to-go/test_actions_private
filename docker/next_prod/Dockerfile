FROM node:20-bullseye-slim AS builder
WORKDIR /app

COPY  ./ /app

RUN npm ci 
RUN npm run build 

FROM node:20-bullseye-slim AS runner
WORKDIR /app

# COPY --from=builder /app/next.config.js ./
# COPY --from=builder /app/public ./public
# COPY --from=builder /app/.next/static ./.next/static
# COPY --from=builder /app/.next/standalone ./

COPY --from=builder /app ./

EXPOSE 3000
ENV PORT 3000
ENV HOSTNAME localhost

CMD npm run start
