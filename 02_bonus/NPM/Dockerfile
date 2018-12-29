FROM node

COPY . /app

WORKDIR /app

RUN npm install

EXPOSE 80

CMD ["npm","start"]

#Commands to use from the app's directory

#docker build -t npmi .
#docker run -ti -p 80:8080 npmi