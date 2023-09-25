---
layout: post
title:  "Music Manager"
pin: true
image:
  path: /resources/img/music-manager/padufy.png
  alt: Music Manager
---
<div markdown="1" style="text-align: justify;">
Music Manager è una semplice applicazione web che ho creato per memorizzare tutte le canzoni che io abbia mai ascoltato e piaciute o che sono andate in trend su Tik Tok.
Il front-end è stato realizzato con [Angular Material](https://material.angular.io/) mentre il back-end è scritto in php. Sulla pagina c'è anche l'opzione di scaricare in formato JSON la delle canzoni. Io personalmente la uso per scaricare le canzoni tramite questo script pyhton:

    # Author: Paduraru Danut Razvan
    import pytube
    import pytube.exceptions
    import json
    import os
    
    # removes illegal characters from file names
    def filename_purifier(path):
        return path.translate({ord(i): None for i in r'[^\w_.-]\',_"'})
    
    
    SCRIPT_FOLDER = os.path.dirname(__file__)
    SONGS_DIR = SCRIPT_FOLDER + "\\songs"
    
    downloaded_songs = []
    songs = []
    error_logs = {"regex_errors": [], "download_errors": []}
    
    if not os.path.exists(SONGS_DIR):
        os.mkdir(SONGS_DIR)
    
    
    for song in [song for song in os.listdir(SONGS_DIR) if song.endswith(".mp3")]:
        downloaded_songs.append(song.removesuffix(".mp3"))
    
    with open(SCRIPT_FOLDER + "\\songs.json", encoding="utf-8") as file:
        songs = json.load(file)
    
    for song in songs:
        title = song["title"]
        link = song["link"]
        if title in downloaded_songs:
            print("Skipping " + title)
            continue
        title = filename_purifier(title)
        try:
            video = pytube.YouTube(link)
            audio = video.streams.filter(only_audio=True).first()
    
            try:
                audio.download(SONGS_DIR, filename=title + ".mp3")
                print("DOWNLOADED: " + title)
            except Exception as e:
                print("FAILED TO DOWNLOAD: " + title)
                error_logs["download_errors"].append({"song": song, "error": str(e)})
        except pytube.exceptions.RegexMatchError as e:
            print("FAILED ID EXTRACTION " + title + " LINK: " + link)
            error_logs["regex_errors"].append({"song": song, "error": str(e)})
    
    with open(
        SCRIPT_FOLDER + "\\error_log.json", encoding="utf-8", mode="w"
    ) as error_log_file:
        json.dump(error_logs, error_log_file)

Per poter eseguire lo script bisogna installare la libreria [Pytube](https://github.com/pytube/pytube). Per installarla basta eseguire questo comando:

    pip install pytube

In breve lo script prima controlla che esista e che file contiene la cartella songs, per poi leggere il JSON delle canzoni, controlla che non siano già state scaricate dentro songs per poi procedere ad usare Pytube per scaricare gli .mp3 .

<div>