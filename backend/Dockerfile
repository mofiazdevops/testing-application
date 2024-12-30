# first stage
FROM node:21 AS backend-builder
                                           # first time full image lana ka purpose yai hai ka < npm dependencies > thk sai instal                                 ho jai phe wo un dependencies ko < /app > ma save kar dai ga .
# ste the working directory
WORKDIR /app

# copy the code source to destination
COPY . .

# install npm / dependencies
RUN npm i
# test intigrate with Dockerfile
RUN npm run test                   
                        # yai hum code sai pata chala hai test ka us ma < test dir > --> backend --> package.json --> test , hai , or npm node.js ka project hai  es lia npm asa chal rha hai 
# stage 2                          # yaha par slim image use kar rhai hai ab < npm dependencies > ka issue nhi ai ga because
FROM node:21-alpine
                                   # ab hum < /app > ko copy krai ga us ma required dependencies hai .
# ste the working directory
WORKDIR /app

# copy the satge first direcoty < /app > where < npm i > dependencies installed
COPY --from=backend-builder /app .

# copy .env.docker file into .env
COPY .env.docker .env

# port expose which  application run
EXPOSE 5000

CMD ["npm", "start"]

