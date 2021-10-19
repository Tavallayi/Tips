# Split an audio file into multiple
This worked for me when I tried it on a mp3 file.

```sh
$ ffmpeg -i somefile.mp3 -f segment -segment_time 3 -c copy out%03d.mp3
```
Where ```-segment_time``` is the amount of time you want per each file (in seconds).

# References
- [Splitting an audio file into chunks of a specified length](https://superuser.com/questions/525210/splitting-an-audio-file-into-chunks-of-a-specified-length)
- [4.22 segment, stream_segment, ssegment - ffmpeg documentation](https://www.ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment)

# Thanks: 
* [slm](https://unix.stackexchange.com/users/7453/slm) for your [answer](https://unix.stackexchange.com/a/283547)
