# Foto Kader PWA

Dit pakket is klaar om als kleine Progressive Web App te hosten.

## Wat zit erin
- Camera rechtstreeks in de app via `getUserMedia`
- Geen extra Samsung "foto gebruiken / opnieuw"-stap vanuit de native camera-app
- Groene, oranje en rode kaders
- Kaders selecteren, verslepen en via hoekpunten vergroten/verkleinen
- Selectie verwijderen / alles verwijderen
- Tijdelijke modus "Kleur aanpassen"
- JPG lokaal opslaan
- PWA-manifest met app-icoon
- Service worker zodat de app na eerste succesvolle online laadbeurt offline kan openen

## Online zetten
Upload alle bestanden in deze map naar één HTTPS-site, bijvoorbeeld GitHub Pages.

Belangrijk: de camera via `getUserMedia` werkt op een beveiligde context (HTTPS). Na installatie/cache kan de app offline blijven werken, terwijl de app-origin dezelfde HTTPS-origin blijft.

## Installeren op Samsung / Chrome
1. Open de HTTPS-link in Chrome.
2. Geef cameratoestemming wanneer gevraagd.
3. Gebruik "Installeren" als die knop verschijnt, of Chrome-menu > Installeren / Toevoegen aan startscherm.
4. Open de app nadien via het app-icoon.
5. Test offline door vliegtuigmodus aan te zetten nadat de app minstens één keer volledig online geopend is.

## Bestanden
- index.html
- manifest.webmanifest
- service-worker.js
- icon-192.png
- icon-512.png


## Versie 2
- Probeert continue autofocus te activeren als camera + browser dit ondersteunen.
- Gebruikt `ImageCapture.takePhoto()` voor een echte still photo wanneer beschikbaar.
- Valt automatisch terug op een hoog-resolutie videoframe als still capture niet beschikbaar is.
- Flitsknop in de camera: Uit / Auto / Flits, afhankelijk van de capabilities.
- Als echte flash niet beschikbaar is maar torch wel, gebruikt Flits kort de LED als fallback.


## Versie 3 – native smartphonecamera
- De ingebouwde webcamera is verwijderd.
- `Foto nemen` opent via `capture="environment"` de normale cameraflow van de smartphone.
- Autofocus, zoom, flits, HDR, belichting en lenskeuze worden dus door Samsung/iPhone/Android zelf afgehandeld.
- Na bevestigen komt de foto terug in Foto Kader voor de bestaande kaderbewerking.
- Foto Kader slaat de onbewerkte opname niet zelf op; alleen bij `Opslaan` wordt de geannoteerde JPG gedownload.
- De editor bewaart tot 4096 px op de langste zijde en exporteert JPEG op kwaliteit 0.96.
