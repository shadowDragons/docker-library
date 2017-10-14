FROM node:7.0.0

RUN npm install -g grunt-cli

WORKDIR /app

RUN git clone https://github.com/mobz/elasticsearch-head.git /app

RUN npm install

COPY Gruntfile.docker.js /app/Gruntfile.docker.js

EXPOSE 9100

CMD ["grunt", "serve", "--gruntfile", "Gruntfile.docker.js"]