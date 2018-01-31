FROM node:8

WORKDIR /src

#Install deps
COPY src/package.json /src/package.json
RUN cd /src && npm install

#Add all source code
ADD src/ /src/
RUN cd /src

#Default command
CMD ["npm","run","prod"]
