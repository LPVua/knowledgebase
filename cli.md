## Convert mov to gif

```bash
brew install ffmpeg
brew install gifsicle
ffmpeg -i in.mov -pix_fmt rgb8 -r 10 output.gif && gifsicle -O3 output.gif -o output.gif
```
