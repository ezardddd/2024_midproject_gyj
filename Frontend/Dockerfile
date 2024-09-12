FROM node:20-alpine

# 애플리케이션 디렉토리 생성 및 권한 설정
RUN mkdir -p /app && chown -R node:node /app

WORKDIR /app

# root 사용자로 전환
USER root

COPY --chown=node:node package*.json ./
RUN npm install --production

COPY --chown=node:node . .

# node 사용자로 다시 전환
USER node

EXPOSE 8000

CMD ["node", "server-backend.js"]