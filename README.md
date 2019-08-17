# doctORS
We build a web application called doctORS that can assist the operating room manager to schedule operating rooms


## 产品截图
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E9%A6%96%E9%A1%B51.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E9%A6%96%E9%A1%B53.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E7%97%85%E4%BA%BA%E9%A1%B52.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E8%B0%83%E5%BA%A6%E9%A1%B51.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E8%B0%83%E5%BA%A6%E9%A1%B52.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E8%B0%83%E5%BA%A6%E9%A1%B53.png)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E8%B0%83%E5%BA%A6%E9%A1%B54.png)


## 预测手术时长部分

主要思路：构造集成机器学习模型，学习数据特征，预测手术时长，同时使用 LIME 模型增加可解释性。

数据特征由患者基本信息（身高、体重、心电图所见等）和手术信息（手术名称、术前小结、术前诊断）构成，特征包括数值型、字符型、分类型的混合格式。由于数据本身存在缺陷，我们首先对数据进行了预处理。清理异常数据之后，基于人群中的统计规律，对医学检验指标数据中的缺失值进行正常均值下的2σ的高斯插值；查阅医学上相关研究的文献之后，深入挖掘提取了可能对手术时长具有显著影响的一些变量（如并发症个数、手术部位、手术技术），然后通过正则表达抽取数据中的文字特征，利用TF-IDF加权词向量编码和独热编码完成了术前小结、心电所得等段落和非段落短句字符型的数值型转换；最后对分类型文本进行独热编码获得完整、规范的数据仓库。
 
基于数据的自身属性，我们分别使用了传统统计模型如KNN、Bayes回归，常见的深度模型如CNN，以及比较流行的集成网络如LightGBM、CatBoost进行预测，并且对多模型进行stacking实验获取最终较好结果。同时使用 LIME 模型分析了不同特征对模型的重要程度通过MSE、MAE、百分比MAE等评价指标评估预测结果，证实我们的模型取得了良好的预测结果。


## 手术调度部分

根据预测手术时长，考虑复苏室床位、手术室清洁时间、主刀医生手术时间冲突等限制，采用遗传算法，以最优化手术室使用效率为目标，采用种马遗传算法，锦标赛选择算子、两点交叉、互换变异的进化方法，最终得到优于传统经验式排班方式的结果。


## 前后端开发

使用基于 React 的 Ant Design 框架编写前端，Flask编写后端。


## 项目海报及展板
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/poster/43AI%20%E5%8D%8E%E4%BD%97.jpeg)
![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/poster/%E5%B1%95%E6%9D%BF%E6%B5%B7%E6%8A%A5.png)


## 项目参加者
组长：王江舟(复旦计算机)

Web开发：李文(同济计算机)、尹舸帆(北邮电子与通信)、张志臻(天津大学软件工程)

单人预测时长：李晓燕(北京大学应用数学)、王霖庶(北京大学基础医学)、颜学谨(中南大学软件工程)

多人手术调度：李晓雯(中山大学流行病与卫生统计)、李文卓(复旦微电子与固体电子学)、李志远(上海交大机械工程)

设计：文君

![image](https://github.com/jiangzhouwang/Deecamp2019_Team43/blob/master/IMG/%E7%85%A7%E7%89%87%E5%A2%99%E5%B1%95%E7%A4%BA.jpeg)

## 鸣谢
森亿智能公司
