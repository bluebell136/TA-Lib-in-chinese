# CDLONNECK

中文名称：好友反攻

用法：总是看跌

调用方法：talib.CDLONNECK(open, high, low, close)

输出：0代表不符合K线形态，-100表示符合形态

## 指标介绍

第一根k线：长阴线

第二根k线：阳线低开，收盘价第一前一天的最低价

## 图例

![onneck](/assets/CDLONNECK_sh600000.png)

## 使用案例

```python
#展示DataFrame中的数据"603787"
df
```

| 日期        | 开盘价   | 最高价   | 收盘价   | 最低价   |
| --------- | ----- | ----- | ----- | ----- |
| 2017/7/19 | 15.17 | 15.37 | 15.21 | 14.9  |
| 2017/7/20 | 15.5  | 16.09 | 15.36 | 15.27 |
| 2017/7/21 | 15.1  | 15.23 | 15.02 | 14.84 |
| 2017/7/24 | 14.8  | 15.24 | 15.12 | 14.61 |
| 2017/7/25 | 15.04 | 15.24 | 15.17 | 15.01 |
| 2017/7/26 | 15.15 | 15.21 | 14.89 | 14.77 |
| 2017/7/27 | 14.91 | 15.49 | 15.34 | 14.86 |
| 2017/7/28 | 15.33 | 15.62 | 15.34 | 15.26 |
| 2017/7/31 | 15.35 | 15.63 | 15.42 | 15.3  |
| 2017/8/1  | 15.5  | 15.65 | 15.53 | 15.31 |
| 2017/8/2  | 15.53 | 15.73 | 15.49 | 15.4  |
| 2017/8/3  | 15.58 | 15.89 | 15.64 | 15.49 |
| 2017/8/4  | 15.6  | 15.65 | 15.07 | 15.05 |
| 2017/8/7  | 15.03 | 15.22 | 15.06 | 15.01 |
| 2017/8/8  | 15.05 | 15.05 | 14.87 | 14.68 |
| 2017/8/9  | 14.76 | 15.02 | 14.76 | 14.72 |
| 2017/8/10 | 14.71 | 14.8  | 14.45 | 14.4  |
| 2017/8/11 | 14.32 | 14.7  | 14.54 | 14.32 |
| 2017/8/14 | 14.43 | 14.68 | 14.67 | 14.43 |
| 2017/8/15 | 14.7  | 15.26 | 15.21 | 14.64 |

```python
# 赋值开、高、收、低价格，np.array格式。
open_p = df['开盘价'].values
high_p = df['最高价'].values
low_p = df['最低价'].values
close_p = df['收盘价'].values
```

```python
# 展示open_p中的数据
open_p
```

```python
array([15.17, 15.5, 15.1, 14.8, 15.04, 15.15, 14.91, 15.33, 15.35, 15.5, 15.53, 15.58, 15.6, 15.03, 15.05, 14.76, 14.71, 14.32, 14.43, 14.7])
```

```python
# 调用函数
talib.CDLONNECK(open_p, high_p, low_p, close_p)
```

```python
array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -100, 0, 0, 0, 0, 0, 0],dtype=int32)
```

## 在A股使用情况

遍历A股所有股票（包含退市），考察从上市至2017年1季度，所有出现

```python
# 展现统计结果
df.groupby(pattern_name)[[str(i)+'天后涨跌幅' for i in 1, 3, 5, 10]].describe()
```

|        |       |   1天后涨跌幅   |   3天后涨跌幅   |   5天后涨跌幅   |  10天后涨跌幅   |
| :----: | :---: | :--------: | :--------: | :--------: | :--------: |
| ONNECK |       |            |            |            |            |
|  -100  | count |   24785    |   24785    |   24785    |   24785    |
|        | mean  | 0.0030131  | 0.0039628  | 0.0064572  | 0.0090524  |
|        |  std  | 0.0465862  | 0.0700716  | 0.0890776  | 0.1170827  |
|        |  min  | -0.2144640 | -0.2718979 | -0.4101652 | -0.5419850 |
|        |  25%  | -0.0132330 | -0.0253161 | -0.0327592 | -0.0475002 |
|        |  50%  | 0.0033440  | 0.0027365  | 0.0037245  | 0.0030817  |
|        |  75%  | 0.0189570  | 0.0316124  | 0.0431042  | 0.0599998  |
|        |  max  | 5.1122520  | 5.2924915  | 5.5770729  | 5.8395267  |