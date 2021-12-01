# Python

[TOC]

## Pandas

```python
import pandas as pd

data = pd.read_excel(filenale)
# 读取之后有很多columns，按名字读取列

# 1. 选取行列
data['column name']  # 按名字读取列 可以列表里面再列表取多列
data[:4]  # 读取前n行
data['column name'].plot()  # 可以直接调matplotlib

.value_counts()  # 统计元素的个数

# 2. 真值判断
complaints['Complaint Type'] == "Noise - Street/Sidewalk"
# 会返回 True or False 的dataframe
# 还可以复杂情况的比较
is_noise = complaints['Complaint Type'] == "Noise - Street/Sidewalk"
in_brooklyn = complaints['Borough'] == "BROOKLYN"

complaints[is_noise & in_brooklyn][['Complaint Type', 'Borough', 'Created Date', 'Descriptor']][:10]  # 选取部分colomn和row
```

## Xlsx

```python
def write_excle(output_file,keywords_tuple):
    k1,k2=keywords_tuple
    workbook = xlsxwriter.Workbook(output_file)
    worksheet = workbook.add_worksheet()

    worksheet.write(1, 0, 'keywords900w_before')
    worksheet.write(1, 1, 'keywords900w_cluster_before')
        
    worksheet.insert_image(idx * 20 + 2,30, pic, {'x_scale': scale, 'y_scale': scale})
    workbook.close()
```

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

