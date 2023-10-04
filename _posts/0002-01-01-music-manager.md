---
layout: post
title:  "Music Manager"
pin: true
image:
  path: /resources/img/music-manager/padufy.png
  alt: Music Manager
---
<div markdown="1" style="text-align: justify;">


Music Manager è una semplice applicazione web che ho creato per memorizzare tutte le canzoni che mi sono piaciute e/o andate in trend su Tik Tok.

# Tecnologie Usate 
Il front-end è stato realizzato con [Angular](https://angular.io/guide/setup-local) e la libreria [Angular Material](https://material.angular.io/). Ho scelto di usare Angular perchè l'applicazione avrebbe dovuto dare modo di riprodurre le canzoni nel sito quindi se esso non fosse stato una [SPA](https://it.wikipedia.org/wiki/Single-page_application), ad ogni modifica nel sito si sarebbe dovuto ricaricare fermando la riproduzione musicale.
Il back-end è scritto in [PHP](https://www.php.net/). Non ho avuto nessuna particolare ragione per usare il PHP, semplicemente avevo già dimestichezza con esso.

# Funzionalità

 - &#x2714; Aggiungere canzoni
 - &#x2714; Scaricare lista delle canzoni formato JSON
 - &#x2718; Ascoltare musica
 - &#x2718; Creare playlist

  
# Scaricare le canzoni
Le canzoni si possono scaricare tramite [questo codice](https://github.com/PettingStrings/padufy_downloader.git) python.
Lo script di default crea una cartella "songs" dentro la cartella di sistema "Musica" di Windows. Se non dovesse trovarla, crea "songs" nella cartella in cui si trova lo script.

Per poterlo eseguire bisogna installare le dipendenze necessarie elencate dentro "requirements.txt" tramite questo comando:

> python -m pip install requirements.txt

Con il nuovo aggiornamento ora la lista delle canzoni viene presa direttamente dall'API senza bisogno di scaricarla.

# Conclusione

Questa applicazione surclasserà Spotify? Non credo proprio. Personalmente mi è più utile perché molte canzoni che ascolto non ci sono Spotify e non voglio nemmeno pagare per ascoltare musica senza interruzioni (sono un programmatore, me le faccio io le app). Sicuramente con più lavoro dietro Music Manager potrebbe diventare completa, infatti avevo iniziato a implementare le playlist e tag, ma ancora una volta mi sono ritrovato stufo di creare un front-end. Tra div che non si centrano e bottoni che non si allineano, trovo molto tedioso creare interfacce web, quindi ho deciso di chiudere qui il progetto. Ho comunque trovato un modo di aggiungere tag alle canzoni, semplicemente li scrivo dopo il titolo.

<div>