FROM node:22-bullseye-slim

ENV PORT=3000

# Install dependencies

RUN apt-get update && apt-get install -y --no-install-recommends curl wget

RUN npm i -g pnpm

# Build app

COPY ../. /app/.

WORKDIR /app

RUN rm -rf /app/node_modules
RUN pnpm install --frozen-lockfile
RUN pnpm run build

# Launch app

WORKDIR /app/build

EXPOSE ${PORT}

ENTRYPOINT ["node", "index.js"]
