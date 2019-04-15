# L2softmax
for intern

## ファイルの説明
preprocess.ipynb : jsonファイルでデータ分割を定義して、画像の前処理を行う  
intern2019_finetune.ipynb : model作成から学習、テストまで行う

## L2-softmaxを用いた異常検知

オックスフォード大学の提供する犬猫の[データセット](http://www.robots.ox.ac.uk/~vgg/data/pets/)を表1.のように分割し、猫を正常値、犬を異常値とみなし、テストデータで存在しない犬種を未知の異常とみなしてrecall>0.999になるように異常値の検出を行った。

表1. データの分割

||test|train|
|---|---|---|
|cat|1896|475|
|dog|71|4907|

## モデル、ハイパーパラメータ

ImageNetでpre-trainedな**VGG16**を使用。

使用したハイパーパラメータを表2. に示す。

表2. ハイパーパラメータなど

||value|
|---|---|
|学習率|1e-4|
|学習方法|Momentum SGD|

## result summary
epoch=10、batchsize=32で学習を行った結果を表3. に示す。  
recall>0.999以上で検出した際の各種統計値を示した。また、モデルの学習と実行を4回行い、平均値と偏差値をそれぞれ記述した。

表3. 学習の結果

||mean|std|
|---|---|---|
|recall|0.999185|7.765725e-12|
|precision|0.986281|3.704233e-03|
|specificity|0.856316|3.932487e-02|
|accuracy|0.984532|7.126074e-03|
