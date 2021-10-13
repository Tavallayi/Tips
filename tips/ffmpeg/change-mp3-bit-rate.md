Change mp3 bit rate to 96k:
```sh
ffmpeg -i input.file -map 0:a:0 -b:a 96k output.mp3
```

# Thanks: 
* [evilsoup](https://superuser.com/users/180990/evilsoup) for your [answer](https://superuser.com/a/553049)
 