FROM node:20-alpine

# PM2 관련 디렉토리 생성 및 권한 설정
RUN mkdir -p /.pm2 && \
    chown -R node:node /.pm2 && \
    chmod -R 777 /.pm2

# 애플리케이션 디렉토리 생성 및 권한 설정
RUN mkdir -p /app && chown -R node:node /app
RUN mkdir -p /app/public/image && chown -R node:node /app/public
WORKDIR /app

# root 사용자로 전환
USER root

COPY --chown=node:node package*.json ./
RUN npm install --production

COPY --chown=node:node . .
RUN npm install -g pm2

# node 사용자로 다시 전환
USER node

EXPOSE 3000

CMD ["pm2-runtime", "start", "server-frontend.js"]