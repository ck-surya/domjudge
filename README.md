# DOMjudge + MariaDB + Nginx + Certbot Docker Setup

## Steps

1. Create docker networks:
   docker network create backend
   docker network create frontend

2. Start MariaDB:
   docker-compose -f mariadb.yml up -d

3. Start DOMjudge:
   docker-compose -f domserver.yml up -d

4. Run Certbot to obtain SSL certs:
   docker-compose -f certbot.yml up

5. Copy certs:
   cp certs/live/test1.indiaicpc.in/fullchain.pem certs/fullchain.pem
   cp certs/live/test1.indiaicpc.in/privkey.pem certs/privkey.pem

6. Start Nginx:
   docker-compose -f nginx.yml up -d

7. Verify site:
   http://test1.indiaicpc.in → redirects to HTTPS
   https://test1.indiaicpc.in → shows DOMjudge

