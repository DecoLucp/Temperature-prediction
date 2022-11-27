## 1. 小组成员：

| 姓名   | 学号       |
| ------ | ---------- |
| 卢成朋 | 1903060321 |
| 王哲杨 | 1903060322 |
| 王梓鉴 | 1903060324 |
| 白皓成 | 1903060312 |
| 陈立群 | 1903060311 |

## 2. 模型分析文档：

### 以"线性回归"的方式来拟合高阶曲线

在拟合数据点时，一般来说，对于一个自变量的，拟合出来是一条直线；对于两个自变量的，拟合出来时一个直平面。这种拟合结果是严格意义上的“线性”回归。但是有时候，采用“曲线”或“曲面”的方式来拟合，能够对训练数据产生更逼近的效果。这就是“高阶拟合”。

`PolynomialFeatures.fit_transform  ` 提供了将一阶数据扩展到高阶数据的方法；

本项目采用了数据中的当日最高温度进行分析，将26天的数据随机选4天作测试集，剩余22天为训练集；然后我们分别使用一阶曲线(直线)、二阶、三阶与四阶曲线进行拟合，并检查拟合效果。

![image-20221127223158220](https://gallery-lucp.oss-cn-beijing.aliyuncs.com/img/202211272232347.png)

> ❗ 由于数据为随机选取，每次运行的图像有偏差
>
> 一阶：黄色
>
> 二阶：绿色
>
> 三阶：蓝色
>
> 四阶：紫色

同时我们还对各阶的R方(r-squared)进行了计算，对线性回归模型的效果进行评估：

综上对比我们发现，一阶拟合R方约为0.181，二阶拟合R方约为-0.341，三阶拟合R方约为 -1.292 ，四阶拟合R方约为-0.688。很显然，得到的拟合R方值并不是随着阶数的增高而增大，同前理，说明日期并不是最高气温的影响因素。这正与我们常识所知的结论相吻合。因此，想要预测天气值就错综而复杂，不得片面考虑一个或为数不多的几个因素，且不应考虑到与气温影响因素无关的影响变量：比如说像上例中所提及的日期等。

![image-20221127223551512](https://gallery-lucp.oss-cn-beijing.aliyuncs.com/img/202211272235549.png)



## 3. Code: 设置运行环境

本项目使用到了`Conda` 做包依赖的管理，使用`Jupyter Notebook` 编写核心程序；
使用到的环境有：`sklearn`、`numpy`、`matplotlib`、`pandas`；

### 1. 使用Conda创建新环境

```bash
conda create -n school_mcm #创建新环境
conda activate school_mcm  #使用新环境
```

### 2. 安装与配置 Jupyter

```bash
(school_mcm) pip install jupyterthemes #安装jupyterthemes
(school_mcm) jt -h #验证安装
(school_mcm) jt -t grade3 -f fira -fs 16 -cellw 90% -ofs 11 -dfs 11 -T #配置
```

![image-20221116154402984](https://gallery-lucp.oss-cn-beijing.aliyuncs.com/img/202211161544057.png)

```
# 安装环境依赖
conda install pandas scikit-learn numpy matplotlib
```