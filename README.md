# 多層パーセプトロンのスクラッチ実装
## 設計の概要
深層学習モデルの理解を深めるためにnumpyライブラリのみで実装してみた。</br>
簡単な３層モデルで数学的理解を深める(MLP.ipynbが対応)</br>
→各層をクラス化して多層モデルを作成(multi_layer.ipynbが対応)

## モデルの構造,原理
各層は線形変換をする層(affine)と活性化関数(今回はrelu)からなる。出力層はsigmoidまたはsoftmax
線形変換ではパラメータとしてW,bが出てきて、z = Wx + b という変換がなされる。</br>
微分のチェインルールを用いてdL/dW, dL/dbを求めるのが肝。</br>
詳しくは下の手書きファイルを参照</br>
[MLP 数式理解.pdf](https://github.com/user-attachments/files/23657760/MLP.pdf)

## 学習結果
minstを用いて学習し、accuracy=0.9764を達成できた。
<img width="567" height="455" alt="Unknown-4" src="https://github.com/user-attachments/assets/70728720-4cec-4c03-9d72-f685549e443b" />
