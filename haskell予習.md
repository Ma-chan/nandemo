再帰関数

Haskellにはforもwhileもない代わりに、再帰関数が用意されている。

最大値は凄い

命令関数でmax関数を定義する場合は、リストの要素を通してループを回して、リストの要素と現在の要素を比較して、より大きい方をmaxに代入する。そして、結果的にはもっとも大きい数がmaxになる。Hakellではパターンマッチによって、再帰をifを多用することなしに記述することができる。

maximum関数
再帰関数を用いて、最大値を求める関数
入力したリストが空であれば、エラーを返す。
リストに１つ要素が入っている場合は、その要素を返す。
maxTailはxを除いた、リストの残りの要素の最大値。
whereで変数宣言をし、maxTailを定義している。
maximum' (x:xs)では、ガードを用いて条件分岐している。
maxTailがxよりも大きい場合、maxTailをxとする。
その他のmaxTailがx以上の値をとる場合は、そのままmaxTailになる。

```
:{
maximum' :: (Ord a) => [a] -> a  
maximum' [] = error "maximum of empty list"  
maximum' [x] = x  
maximum' (x:xs)   
    | x > maxTail = x  
    | otherwise = maxTail  
    where maxTail = maximum' xs  
:}
```

```
maximum' :: (Ord a) => [a] -> a  
maximum' [] = error "maximum of empty list"  
maximum' [x] = x  
maximum' (x:xs) = max x (maximum' xs)  
```



