# 多層パーセプトロンのスクラッチ実装
## 設計の概要
深層学習モデルの理解を深めるためにnumpyライブラリのみで実装してみた。</br>
簡単な３層モデルで数学的理解を深める(MLP.ipynbが対応)</br>
→各層をクラス化して多層モデルを作成(multi_layer.ipynbが対応)

## モデルの構造,原理
各層は線形変換をする層(affine)と活性化関数(今回はrelu)からなる。出力層はsigmoidまたはsoftmax
線形変換ではパラメータとしてW,bが出てきて、z = Wx + b という変換がなされる。</br>
微分のチェインルールを用いてdL/dW, dL/dbを求めるのが肝。</br>

詳しくは下の手書き画像を参照</br>
![20251120_154526000_iOS](https://github.com/user-attachments/assets/681ad08f-619c-438c-a124-b15c5054417b)
![20251120_154601000_iOS](https://github.com/user-attachments/assets/35482cc5-e8e2-4a85-a5a2-532c190fb72b)

## 学習結果
minstを用いて学習し、accuracy=0.9764を達成できた。
<img width="567" height="455" alt="Unknown-4" src="https://github.com/user-attachments/assets/70728720-4cec-4c03-9d72-f685549e443b" />

## ミスりやすいポイント
- 行列積の次元合わせのための転置忘れがち。　次元エラーが出たら大体そこら辺を見返すとうまくいった。
- np.sum,maxとかでaxis=0,1ミス　途中で転置とったりしているから列ごとに作用させる場合と行ごとに作用させる場合があり、そこを混同しがち
