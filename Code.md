

# Mini-Projekt_M169
Webserver-Image über Docker

## Arbeitsverzeichnis erstellen und hineinnavigieren
`mkdir MiniProjekt`   
`cd MiniProjekt`   

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

## Dockerfile erstellen
`nano Dockerfile`   

## Docker file Inhalt
Basisimage  
`FROM nginx`  
Port exportieren, um nachher darauf zugreifen zu können   
`EXPOSE 8080`   
Starten von Apache auf dem Port 8080   
`CMD ["httpd", "-D", "FOREGROUND"]`  

## Dockerfile bauen
`docker build -t apache169 .`
* docker build: Befehl zum Bauen eines Docker-Images
* -t: Imagename (apache_MIN169)
* .: aktuelles Verzeichnis

## Überprüfung ob Dockerfile erfolgreich gebaut wurde
`docker images`

## Container starten
`docker run -d -p 8080:80 -v $(pwd)/html:/usr/local/apache2/htdocs --name apache-container apache_MIN169`
* docker run: erstellt & startet neuen Container
* -d: detached-Modus (im Hintergrund)
* -p: Portweiterleitung
* --name: weist Container Namen zu
* my-nginx: Imagename

## Überprüfung ob Container läuft
`docker ps`

## Website aufrufen
http://localhost:8080
