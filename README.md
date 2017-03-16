# ffmpeg docker image


## Stabilize

```
ffmpeg -i in.mp4 -vf vidstabdetect=stepsize=6:shakiness=8:accuracy=9:result=transform_vectors.trf -f null -
docker run -ti -v ~/Downloads/gopro/:/tmp/workdir ffmpeg -i in.mp4 -vf vidstabtransform=input=transform_vectors.trf:zoom=1:smoothing=30,unsharp=5:5:0.8:3:3:0.4 -vcodec libx264 -preset slow -tune film -crf 18 -acodec copy out_stable.mp4
```

## Cut

```
docker run -ti -v ~/Downloads/gopro/:/tmp/workdir ffmpeg -ss 00:00:10.000 -i GOPR0472.MP4 -t 20 -c copy out.mp4
```
