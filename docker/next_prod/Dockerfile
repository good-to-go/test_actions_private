FROM node:20-bullseye-slim AS builder
WORKDIR /app

COPY  ./ /app

RUN yarn install --frozen-lockfile
RUN yarn build 

FROM node:20-bullseye-slim AS runner
WORKDIR /app

# COPY --from=builder /app/next.config.js ./
# COPY --from=builder /app/public ./public
# COPY --from=builder /app/.next/static ./.next/static
# COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/public ./public
COPY --from=builder /app/.next/static ./.next/static
COPY --from=builder /app/.next/standalone ./

EXPOSE 3000
ENV PORT 3000
ENV HOSTNAME localhost

# CMD yarn start
CMD ["node", "server.js"]
