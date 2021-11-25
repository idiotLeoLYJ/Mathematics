# Python

[TOC]

## Pandas

```python
import pandas as pd

data = pd.read_excel(filenale)

# 读取之后有很多columns，按名字读取列
```

## Xlsx



## Datetime

```python
from datetime import datetime

time.strptime('Sat Feb 04 14:06:42 2017', '%a %b %d %H:%M:%S %Y')

results[0][0] -> '2021-04-14/\n12:46:03'
a = time.strptime(results[0][0].replace('/\n', ' '), '%Y-%m-%d %H:%M:%S')
a => time.struct_time(tm_year=2021, tm_mon=4, tm_mday=16, tm_hour=15, tm_min=58, tm_sec=40, tm_wday=4, tm_yday=106, tm_isdst=-1)

b = time.strftime('%Y/%m/%d %H:%M:%S', a)
b => '2021/04/16 15:58:40'
```

