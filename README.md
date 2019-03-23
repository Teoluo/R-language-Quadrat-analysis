# R-language-Quadrat-analysis-AND-KDE
## Quadrat-analysis
### 样方分析步骤
- 研究区域中打上网格
- 确定每个网格中点的个数
- 计算均值(Mean)、方差(Var)和方差均值比:VMR=Var/Mean

### 代码解释
#### 1. 建立网格
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/code1.png)
####    网格效果
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/1.png)
#### 2. 添加属性
选择GPA大于3.3的数据，将大于设定的属性值为1，低于设定的属性值为0
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/code2.png)
####    网格效果
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/Qa1.png)
#### 3. 计算结果 
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/code3.png)

- 总样方数： n = 6
- 平均数：   mean = 2.666667
- 方差：     variance = 1.466667
- VMR：      VMR = 0.55

### VMR 结果判断依据
- 对于均匀分布，方差等于0，因此VMR的期望值= 0；
- 对于随机分布，方差等于均值，因此VMR的期望值= 1；
- 对于聚集分布，方差大于均值。因此VMR的期望值 >1 。

### 结论
通过计算，方差为1.47，平均值为2.67，方差于平均值的比值为0.55，介于0-1之间，但又偏向于1，初步设定为随机分布。

## Kernel Density Estimation, KDE
### 分析步骤
- 处理数据
- 选取带宽
- 计算密度

### 代码解析
#### 1. 建立的网格相同

#### 2. 通过对于density函数的参数设置

![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/code4.png)

### 结果
![img](https://github.com/cuit201608/Team1_coding/blob/master/1st/screenshots/KDE.png)

# R-language Moran's l
Moran's I by R-language

## 莫兰指数
莫兰指数一般是用来度量空间相关性的一个重要指标。
莫兰指数是一个有理数，经过方差归一化之后，它的值会被归一化到-1.0——1.0之间。

## 判断依据
Moran's I > 0  表示空间正相关性，其值越大，空间相关性越明显，
Moran's I < 0  表示空间负相关性，其值越小，空间差异越大，
Moran's I = 0，空间呈随机性。

## 代码解析
建立网格，转换成空间点数据类型，通过导入数据，选择GPA大于设定值3.3的，记录坐标信息以及GPA</br>
**knearneigh**：返回的是最近的K个邻居</br>
**dnearneigh** ：是通过最近距离和最远距离来选取相应的邻居</br>
我们选取dnearneigh来选取邻居，再使用计算莫兰指数的代码

![img](https://github.com/Teoluo/R-language-Quadrat-analysis-AND-KDE/blob/master/morans/screenshots/code.png)

## 结果
![img](https://github.com/Teoluo/R-language-Quadrat-analysis-AND-KDE/blob/master/morans/screenshots/1.png)
![img](https://github.com/Teoluo/R-language-Quadrat-analysis-AND-KDE/blob/master/morans/screenshots/moran.png)

## 结论
计算出来的莫兰指数为**0.04463434**，数据大于零，其值极其接近于零，我们认为它具有**随机性**，但有一丝的空间正相关，可能会存在一少部分相关的几率。
