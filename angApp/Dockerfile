FROM node:20-alpine as builder

WORKDIR '/app'
COPY package.json .

RUN npm --loglevel verbose install --dev

RUN npm --loglevel verbose install -g @angular/cli
COPY . .

RUN ng build

FROM nginx
COPY --from=builder /app/dist /usr/share/nginx/html