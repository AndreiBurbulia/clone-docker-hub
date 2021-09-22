# boolgram

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


# Istruzione per far girare l'app in docker

#### 1)	Andare a visitare Docker Hub dove si trova la repository con l’immagine 
####    	https://hub.docker.com/r/andreiburbulia/boolgram

#### 2)	Aprire il terminale del proprio pc
#### 3) Tornare nella pagina sopra e copiare il commando “Docker Pull Command”  
#### 4)Tornare nel terminale ed incollare  e far girare il seguente commando:
```
	docker pull andreiburbulia/boolgram
```

#### 5)	Sempre nel terminale digitare 
```
docker image ls
```

#### Per verificare se l’immagine e stata importata
#### 6) Ora dobbiamo avviare l’immagine in un container per poter visualizzare il tutto quindi nel terminale digitiamo:
```
docker run -it -p 8080:8080 –rm –name boolgram-app andreiburbulia/boolgram
```
#### una volta finite di compilare ci appariranno gli indirizzo in locale dove visualizzare il progetto quindi andare all’indirizzo mostrato, in questo caso http://127.0.0.1:8080
#### a questo indirizzo sarà visibile il progetto