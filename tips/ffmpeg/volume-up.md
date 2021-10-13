# Audio Volume Manipulation
## Changing volume
To change the audio volume, you may use FFmpeg's ​volume audio filter.

If we want our volume to be half of the input volume:
```sh
ffmpeg -i input.wav -filter:a "volume=0.5" output.wav
```
150% of current volume:

```sh
ffmpeg -i input.wav -filter:a "volume=1.5" output.wav
```

You can also use decibel measures. To increase the volume by 10dB:

```sh
ffmpeg -i input.wav -filter:a "volume=10dB" output.wav
```
To reduce the volume, use a negative value:

```sh
ffmpeg -i input.wav -filter:a "volume=-5dB" output.wav
```
Note that the volume filter only adjusts the volume. It does not set the volume. To set or otherwise normalize the volume of a stream, see the sections below.

## Peak and RMS Normalization
To normalize the volume to a given peak or RMS level, the file first has to be analyzed using the volumedetect filter:

```sh
ffmpeg -i input.wav -filter:a volumedetect -f null /dev/null
```
Read the output values from the command line log:

```log
[Parsed_volumedetect_0 @ 0x7f8ba1c121a0] mean_volume: -16.0 dB
[Parsed_volumedetect_0 @ 0x7f8ba1c121a0] max_volume: -5.0 dB
...
```
... then calculate the required offset, and use the volume filter as shown above.

## Reference
[Audio Volume](https://trac.ffmpeg.org/wiki/AudioVolume)