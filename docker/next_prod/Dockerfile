FROM node:18.15-slim AS builder
WORKDIR /app

COPY  ./ /app

ENV NODE_ENV production
RUN yarn install --frozen-lockfile
RUN yarn build 

FROM node:18.15-slim AS runner
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
