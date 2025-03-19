

# Mini-Projekt_M169
Webserver-Image über Docker

## Arbeitsverzeichnis erstellen
`mkdir MiniProjekt`  
* erstellt Verzeichnis  
`cd MiniProjekt`   
* navigiert in das Verzechnis

## Dockerfile erstellen
`nano Dockerfile`   

## Docker file Inhalt
#Basisimage  
`FROM nginx`  
#kopiert index.html Datei in das Web-Root-Verzechnis des Containers  
`COPY index.html /usr/share/nginx/html/`   


## index.html Inhalt
`<!doctype html>`  
`<html lang="en">`  
 ` <head>`  
 `   <meta charset="UTF-8" />`  
  `  <meta name="viewport" content="width=device-width, initial-scale=1.0" />`  
  `  <title>Hello Docker!</title>`  
  `</head>`  
 ` <body>`
  `  <h1>Hello Docker!</h1>`
  `  <p>This is a custom Docker image.</p>`
 ` </body>`
`</html>`

## Dockerfile bauen
`docker build -t my-nginx .`
* docker build: Befehl zum Bauen eines Docker-Images
* -t: Imagename (my-nginx)
* .: aktuelles Verzeichnis

## Überprüfung ob Dockerfile erfolgreich gebaut wurde
`docker images`
Bild)

## Docker Volume erstellen
`docker volume create nginx-config`


## Container starten
docker run -d --name nginx -v /home/vmadmin/MiniProjekt/VOL/config:/etc/nginx/conf.d -v /home/vmadmin/MiniProjekt/VOL/logs:/var/log/nginx -p 8080:80 my-nginx


`docker run -d -p 8080:80 --name my-nginx-container my-nginx`
* docker run: erstellt & startet neuen Container
* -d: detached-Modus (im Hintergrund)
* -p: Portweiterleitung
* --name: weist Container Namen zu
* my-nginx: Imagename

## Überprüfung ob Container läuft
`docker ps`

## Website aufrufen
http://localhost:8080

## TODO
VOLUME für Log und für Config erstellen
INDEX.HTML ausserhalb nicht hineineladen

