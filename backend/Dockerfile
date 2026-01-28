FROM node:18-alpine

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy application source
COPY . .

# Expose the port Railway provides
ENV PORT=10000
EXPOSE 10000

CMD ["node", "server.js"]
