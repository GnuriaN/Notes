**youtube-dl** — утилита для загрузки потокового видео с видеохостингов, таких как youtube. Эта утилита поддерживает загрузку с множества видеохостингов, помимо YouTube, что собственно понятно с названия, а тажке и другие [сайты](http://rg3.github.io/youtube-dl/supportedsites.html).

Ссылка на сайты [http://rg3.github.io/youtube-dl](http://rg3.github.io/youtube-dl/)

### Несколько примеров использования:

`youtube-dl -F <url>` - получаем все позможные форматы по ссылке

Пример:
```console
youtube-dl -F https://youtu.be/wRGW9dkzh-E
[youtube] wRGW9dkzh-E: Downloading webpage
[youtube] wRGW9dkzh-E: Downloading video info webpage
[youtube] wRGW9dkzh-E: Extracting video information
[info] Available formats for wRGW9dkzh-E:
format code  extension  resolution note
249          webm       audio only DASH audio   57k , opus @ 50k, 19.06MiB
250          webm       audio only DASH audio   73k , opus @ 70k, 24.29MiB
171          webm       audio only DASH audio  109k , vorbis@128k, 36.53MiB
251          webm       audio only DASH audio  130k , opus @160k, 44.19MiB
140          m4a        audio only DASH audio  130k , m4a_dash container, mp4a.40.2@128k, 47.38MiB
160          mp4        256x144    144p   53k , avc1.4d400c, 30fps, video only, 9.05MiB
133          mp4        426x240    240p   88k , avc1.4d4015, 30fps, video only, 15.32MiB
278          webm       256x144    144p  109k , webm container, vp9, 30fps, video only, 28.84MiB
242          webm       426x240    240p  177k , vp9, 30fps, video only, 30.63MiB
134          mp4        640x360    360p  210k , avc1.4d401e, 30fps, video only, 32.99MiB
243          webm       640x360    360p  324k , vp9, 30fps, video only, 54.07MiB
135          mp4        854x480    480p  383k , avc1.4d401f, 30fps, video only, 59.63MiB
244          webm       854x480    480p  497k , vp9, 30fps, video only, 81.24MiB
136          mp4        1280x720   720p  626k , avc1.4d401f, 30fps, video only, 100.12MiB
247          webm       1280x720   720p  902k , vp9, 30fps, video only, 149.58MiB
137          mp4        1920x1080  1080p 1082k , avc1.640028, 30fps, video only, 171.09MiB
248          webm       1920x1080  1080p 1703k , vp9, 30fps, video only, 260.57MiB
17           3gp        176x144    small , mp4v.20.3, mp4a.40.2@ 24k
36           3gp        320x180    small , mp4v.20.3, mp4a.40.2
43           webm       640x360    medium , vp8.0, vorbis@128k
18           mp4        640x360    medium , avc1.42001E, mp4a.40.2@ 96k
22           mp4        1280x720   hd720 , avc1.64001F, mp4a.40.2@192k (best)
```

Если мы выполним `youtube-dl -cio "%(autonumber)s-%(title)s.%(ext)s" -f 137 https://youtu.be/wRGW9dkzh-E`то получим:
```console
[youtube] wRGW9dkzh-E: Downloading webpage
[youtube] wRGW9dkzh-E: Downloading video info webpage
[youtube] wRGW9dkzh-E: Extracting video information
[download] Destination: 00001-Как стать GPU-инженером за час _ Технострим.mp4
[download] 100% of 171.09MiB in 00:53
```
но в нем нет аудио, так как это `video only` мы можем скачать отдельно `m4a` используя параметр `-f 137+140`, и получаем на выходе два файла `"00001-Как стать GPU-инженером за час _ Технострим.f137.mp4"` и `"00001-Как стать GPU-инженером за час _ Технострим.f140.m4a"`. После этого, используя утилиту [FFmpeg](http://ffmpeg.org/) мы склеивам эти файлы:
`ffmpeg -i "00001-Как стать GPU-инженером за час _ Технострим.f137.mp4" -i "00001-Как стать GPU-инженером за час _ Технострим.f140.m4a" out.mp4`
и получаем готовый файл.
