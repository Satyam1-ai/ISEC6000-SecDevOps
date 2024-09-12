# Base image
FROM node:20-alpine AS base

# Install libc6-compat for compatibility
RUN apk add --no-cache libc6-compat

WORKDIR /app

# Enable corepack to manage pnpm automatically
RUN corepack enable

# Copy the package files before running pnpm install
COPY package.json pnpm-lock.yaml ./

# Use pnpm to install dependencies
RUN corepack prepare pnpm@9.6.0 --activate && pnpm install --frozen-lockfile --prefer-offline

# Rebuild the source code only when needed
FROM base AS builder

WORKDIR /app
COPY --from=base /app/node_modules ./node_modules
COPY . .

# Set environment variables for the API and Storefront URLs
ARG NEXT_PUBLIC_SALEOR_API_URL
ENV NEXT_PUBLIC_SALEOR_API_URL=${NEXT_PUBLIC_SALEOR_API_URL}
ARG NEXT_PUBLIC_STOREFRONT_URL
ENV NEXT_PUBLIC_STOREFRONT_URL=${NEXT_PUBLIC_STOREFRONT_URL}

# Build the application
RUN pnpm build

# Production image, copy necessary files and run Next.js in production mode
FROM node:20-alpine AS runner

WORKDIR /app

COPY --from=builder /app/.next ./.next
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./package.json

# Set the environment variables for production
ENV NODE_ENV production
ENV PORT 3000

EXPOSE 3000

# Start Next.js in production mode
CMD ["pnpm", "start"]
