FROM node:16 AS development

# Specify Working directory inside container
WORKDIR /project/src/app

COPY package*.json ./

RUN npm install

# Bundle App Sources
COPY . .

RUN npm run build


EXPOSE 3000

################
## PRODUCTION ##
################
# Build another image named production
FROM node:16 AS production

ARG NODE_ENV=production
ENV NODE_ENV=#{NODE_ENV}

# Set work dir

WORKDIR /project/src/app

COPY --from=development /project/src/app/ a.

EXPOSE 8080

# run app
CMD [ "node", "dist/main" ]