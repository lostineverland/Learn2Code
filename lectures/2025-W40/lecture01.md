# Lecture 1: Working Environment

- Setup Discord Channel
- Setup GitHub Codespaces
- CLI
  - today we're going to learn about the terminal
  - it used to be that _was_ the computer
  - start w/ tour of my computer
  - home
  - desktop


## Homework

Use the following prompt on your Co-pilot AI in Github Codespaces:

```txt
I'm learning to code and I will be using Github Codespaces as my working environment. I'm unfamiliar with Unix/Linux or the CLI (command line interface). I need to learn the following commands:
  - pwd
  - ls
  - cp
  - mv
  - rm
  - mkdir
  - rmdir
  - cd
  - echo
  - touch
  - cat
  - less
  - tree
  - man

Can you help me learn these commands through the course of multiple lessons, and in an order which makes sense (not necessarily in the order presented here)? Please give me several examples in the context of Github Codespaces, after which I may have follow up questions. Don't move to the next lesson until I explicitly say "next lesson".
```

## Notes

I looked at my own terminal history to pull the commands that I use most frequently, then cleaned it up a bit. This is what I used:

Pull the history into a file that I can parse
```sh
history > /Users/carlos/Documents/2025/Learn2Code/mycommands.txt
```

Run python to find the command frequency and sort
```py
uv run python
from collections import Counter
import json

def history():
  with open('/Users/carlos/Documents/2025/Learn2Code/mycommands.txt') as f:
    for i in f:
      yield i

stripCMD = lambda i: i.split()[3]
cmds = list(map(stripCMD, history()))
c = Counter(cmds)
cmd_freq = dict(
  sorted(
    [(k, v) for k, v in c.items() if v > 30],
    key=lambda i: i[1],
    reverse=True
  ))

print(json.dumps(cmd_freq, indent=2))
```
