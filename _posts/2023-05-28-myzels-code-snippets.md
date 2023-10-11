---
layout: article
title: "Myzel keeps misplacing or deleting code snippets"
author: myzel
---

This is one that myzel just made and now is getting a post all for its own because i have no other place where to put it and its funnier this way.

Also, we found this thing called [GPT4ALL](https://github.com/nomic-ai/gpt4all) and it's quite an amazing thing because we can feed it a text corpus and it'll chew on it before every answer.

<!--more-->

```python
from tqdm.auto import tqdm

miab = open("STORY DOWNLOADED FROM FIMFICTIONDOTNET HERE.txt", 'r', encoding='utf-8').read().splitlines()

f = True
fi = ""
ctr = 0

dtx = {}

for line in tqdm(miab, leave=True, desc="Reading MIAB"):
    if line.startswith("> "):
        if f:
            f       = False
            ctr    += 1
            fi      = str(ctr) + line.replace("> ", " - ") + ".txt"
            dtx[fi] = []
            tqdm.write(str(fi))
        else: continue
    else:
        f = True
        if line: dtx[fi].append(line)

for name, chapter in tqdm(dtx.items(), leave=True, desc="Writhing Files"):
    if chapter:
        with open(name.replace(':', '_'), 'w', encoding="utf-8") as of:
            of.write('\n'.join(chapter))
```

