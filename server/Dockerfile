FROM node:21.4.0

RUN mkdir -p /opt/app

ENV NODE_ENV production

RUN apt-get -q update && apt-get -qy install netcat-openbsd
RUN npm i npm@latest -g
RUN npm install -g nodemon

WORKDIR /opt
COPY package.json package-lock.json* ./
RUN npm install && npm cache clean --force
ENV PATH /opt/node_modules/.bin:$PATH

WORKDIR /opt/app
COPY . /opt/app

CMD ["nodemon", "index.js"]

EXPOSE 5000
