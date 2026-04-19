|           | 陰性判定    | 陽性判定    |
| --------- | ------- | ------- |
| **陰性クラス** | TN(真陰性) | FP(偽陽性) |
| **陽性クラス** | FN(偽陰性) | TP(真陽性) |

##### 適合率
$precision = \frac{TP}{TP + FP}$
陽性と判定されたうちの真陽性の割合
「当たりと言ったときの正しさ」

##### 再現率
$recall = \frac{TP}{TP+FN}$
陽性グラス(真陽性+偽陰性)のうち陽性と判定された割合
「当たりを見逃さない力」
##### F値
適合率と再現率の調和平均（調和平均は小さい値に強く引っ張られて小さくなる）
$F = \frac{2}{\frac{1}{precision} + \frac{1}{recall}} = 2*\frac{precision*recall}{precision+recall} = \frac{TP}{TP + \frac{FN+TP}{2}}$
