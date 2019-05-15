再帰関数

Haskellにはforもwhileもない代わりに、再帰関数が用意されている。

最大値は凄い

命令関数でmax関数を定義する場合は、リストの要素を通してループを回して、リストの要素と現在の要素を比較して、より大きい方をmaxに代入する。そして、結果的にはもっとも大きい数がmaxになる。

maximum関数
再帰関数を用いて、最大値を求める関数
入力したリストが空であれば、エラーを返す。
リストに１つ要素が入っている場合は、その要素を返す。


```
maximum' :: (Ord a) => [a] -> a  
maximum' [] = error "maximum of empty list"  
maximum' [x] = x  
maximum' (x:xs)   
    | x > maxTail = x  
    | otherwise = maxTail  
    where maxTail = maximum' xs  
```

