# Aggiunge la sezione video al sito HTML aggiornato
animated_with_video_html = animated_html.replace(
    '</div>\n</body>',
    '''
    <div class="section" id="video">
        <h2>Video del Clan</h2>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/kBbqK8T-tUI" frameborder="0" allowfullscreen></iframe>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/oCiEcfAHLFo" frameborder="0" allowfullscreen></iframe>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/Eq9nofqe0Is" frameborder="0" allowfullscreen></iframe>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/x7xvfRksDmw" frameborder="0" allowfullscreen></iframe>
    </div>
</div>
</body>'''
)

# Nuovo percorso per la versione con video
updated_with_video_dir = "/mnt/data/godz_clan_site_animated_with_video"
os.makedirs(updated_with_video_dir, exist_ok=True)

# Scrive il nuovo file HTML con i video
video_index_path = os.path.join(updated_with_video_dir, "index.html")
with open(video_index_path, "w") as f:
    f.write(animated_with_video_html)

# Copia il logo anche in questa cartella
new_logo_path_with_video = os.path.join(updated_with_video_dir, "logo-godz-clan.jpg")
os.system(f"cp '{original_logo_path}' '{new_logo_path_with_video}'")

# Crea un nuovo ZIP con i video inclusi
video_zip_path = "/mnt/data/godz_clan_site_animated_with_video.zip"
with ZipFile(video_zip_path, 'w') as zipf:
    zipf.write(video_index_path, arcname="index.html")
    zipf.write(new_logo_path_with_video, arcname="logo-godz-clan.jpg")

video_zip_path
# Aggiunge una canzone vichinga in autoplay con controlli audio nel sito

# Inserisce tag audio con una traccia vichinga da YouTube (tramite file mp3 esterno)
html_with_music = section_images_html.replace(
    "<body>",
    '''
    <body>
    <audio autoplay loop controls style="position: fixed; top: 10px; right: 10px; z-index: 1000;">
        <source src="https://dl.sndup.net/kx9n/Viking_Music_Battle.mp3" type="audio/mpeg">
        Il tuo browser non supporta l'audio HTML5.
    </audio>
    '''
)

# Cartella per la versione finale con audio
music_site_dir = "/mnt/data/godz_clan_site_with_music"
os.makedirs(music_site_dir, exist_ok=True)

# Scrive file HTML aggiornato
music_index_path = os.path.join(music_site_dir, "index.html")
with open(music_index_path, "w") as f:
    f.write(html_with_music)

# Copia logo
music_logo_path = os.path.join(music_site_dir, "Logo_del_Clan_GD.png")
os.system(f"cp '{new_logo_path}' '{music_logo_path}'")

# Crea ZIP finale con musica
music_zip_path = "/mnt/data/godz_clan_site_with_music.zip"
with ZipFile(music_zip_path, 'w') as zipf:
    zipf.write(music_index_path, arcname="index.html")
    zipf.write(music_logo_path, arcname="Logo_del_Clan_GD.png")

music_zip_path
