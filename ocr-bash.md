# For OS X
```
brew install tesseract
brew install pngpaste
```
1. Take a snippet with `cmd + shift + ctrl + 4`
2. `pngpaste /tmp/img.png && tesseract /tmp/img.png /tmp/img && cat /tmp/img.txt | pbcopy`
3. Hope for the best, try different tesseract options to improve the chances.
