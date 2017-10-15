FROM node:7.0.0

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
    echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib" >/etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list

RUN npm install -g grunt-cli

WORKDIR /app

RUN git clone https://github.com/mobz/elasticsearch-head.git /app

RUN npm install

COPY Gruntfile.docker.js /app/Gruntfile.docker.js

COPY docker-entrypoint.sh /

EXPOSE 9100
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["grunt", "server", "--gruntfile", "Gruntfile.docker.js"]