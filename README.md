# Dockerized Vue App

# vue-app


Dockerfile: 


#Fetching the latest node image on alpine linux

	FROM node:18-alpine
	
#install simple http server for serving static content

	RUN npm install -g http-server
	
#make the 'app' folder the current working directory

	WORKDIR /app
	
#copy 'package.json' to install dependencies

	COPY package*.json ./
	
#install dependencies

	RUN npm install
	
#copy files and folders to the current working directory (i.e. 'app' folder)

	COPY . .
	
#build app for production with minification

	RUN npm run build
	EXPOSE 8080
	CMD [ "http-server", "dist" ]
	

----- X -----






#Building image

	docker build . -t dockerized_vue

#Running container

	docker run --name vue-app -p 8080:8080 -d dockerized_vue

#On Browser

	http://localhost:8080
	
	
	
	
	
	
	
# Vue

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
