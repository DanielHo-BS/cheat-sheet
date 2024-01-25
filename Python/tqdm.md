# tqdm

## Introduction

``tqdm`` means "progress" in Arabic (taqadum, تقدّم) and is an abbreviation for "I love you so much" in Spanish (te quiero demasiado).

## Usage

```python
from tqdm import tqdm

# first way
for i in tqdm(range(10000)):
    pass

# second way
# update 1 every time by yourself
with tqdm(total=10000) as pbar:
    for i in range(10000):
        pbar.update(1)  # or pbar.update()

# third way
# iterable object
a = [1, 2, 3, 4, 5]
for i in tqdm(a):
    pass
```

## Reference

[使用 tqdm by Clay](https://clay-atlas.com/blog/2019/11/11/python-chinese-tutorial-tqdm-progress-and-ourself/)

[tqdm document](https://tqdm.github.io/)