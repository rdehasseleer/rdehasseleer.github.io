---
title: "Random periodic background"
date: 2025-08-09
tags: [bash]
author: "Romain Dehasseleer"
---

---

### Random periodic background
```bash 
#!/bin/bash
while true; do

    if [ -f wallpaperRandomUnsplash.jpg ]; then 
        rm wallpaperRandomUnsplash.jpg
    fi

    wget https://unsplash.it/1920/1080/?random >/dev/null 2>&1

    mv ./index.html?random ./wallpaperRandomUnsplash.jpg

    feh --bg-scale wallpaperRandomUnsplash.jpg
    sleep 600
done
```

Add to `~/.config/i3/config` :

```bash
exec --no-startup-id path-to-script.sh
```