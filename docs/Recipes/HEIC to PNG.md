# HEIC to PNG converter (not tested)

as per [this StackOverflow post](https://apple.stackexchange.com/a/347507/366515).
```bash
# install imagemagick
brew install imagemagick

# convert a single image
magick convert foo.HEIC foo.jpg

# bulk convert multiple images
magick mogrify -monitor -format jpg *.HEIC
```
`