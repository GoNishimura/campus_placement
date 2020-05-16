# campus_placement

Please watch [report.ipynb](https://github.com/GoNishimura/campus_placement/blob/master/report.ipynb)
for details.

  
# データの概要
## Placement data of students in Jain University Bangalore
## The goal is to classify the students who was getting placed by corporate (Placed: 0, Not placed: 1).

data obtained from:
https://www.kaggle.com/benroshan/factors-affecting-campus-placement

  
# 結果

|No data augumentation|positive|negative|
|:-|:-|:-|
|true|29|2
|false|4|8
  
|With data augumentation|positive|negative|
|:-|:-|:-|
|true|25|6
|false|2|10
  
||With augumentation|No augumentation|augumentation effect|
|:-|:-|:-|:-|
|ROC|0.819892|0.801075|0.018817
|ACC|0.813953|0.860465|-0.046512
|F1|0.714286|0.727273|-0.012987
|recall|0.833333|0.666667|0.166667
|precision|0.625000|0.800000|-0.175000

  
# 考察

SMOTEで足りなかったNot Placedが足された（セル3と10を参照）ことによって、
- ROC(真陽性(TP)と偽陽性(FP)についての指標)とrecall（TP / (TP + FN)）が上昇したが、
- accuracy((TP + TN) / (TP + TN + FP + FN))とprecision(TP　/　(TP　+　FP))、F1(precisionとrecallの調和平均)が減少した。

予測が全体としてNegativeに偏ってPositiveに対して弱くなっており、きちんと教師データにfalseが増えたことを反映した結果になっている。  
ただ、指標上ではスコアが下がってしまったものが多く、上がったものも上がり幅がそれほど大きくなく、今回に関してはdata augumentationをしなくても良かったと思われる。
