# let it be 

円柱の表面積を求める

```
:{
cylinder :: (RealFloat a) => a -> a -> a  
cylinder r h = 
    let sideArea = 2 * pi * r * h  
        topArea = pi * r ^2  
    in  sideArea + 2 * topArea  
:}
```

```
:{
ghci> [if 5 > 3 then "Woo" else "Boo", if 'a' > 'b' then "Foo" else "Bar"]  
["Woo", "Bar"]  
ghci> 4 * (if 10 > 5 then 10 else 0) + 2  
42  
:}

```

```
ghci> 4 * (let a = 9 in a + 1) + 2  
42  
```

```
ghci> [let square x = x * x in (square 5, square 3, square 2)]  
[(25,9,4)]  
```

# 再帰関数

Haskellにはforもwhileもない代わりに、再帰関数が用意されている。

## 最大値は凄い

命令関数でmax関数を定義する場合は、リストの要素を通してループを回して、リストの要素と現在の要素を比較して、より大きい方をmaxに代入する。そして、結果的にはもっとも大きい数がmaxになる。Hakellではパターンマッチによって、再帰をifを多用することなしに記述することができる。
let関数

### maximum関数

maximum関数とは、再帰関数を用いて、最大値を求める関数である。
maximum関数はOrdering型(順番つける)のリストを受け取って、リストの要素内の数字で最も大きい値を返す。


アルゴリズム

入力したリストが空であれば、エラーを返す。
リストに１つ要素が入っている場合は、その要素を返す。
maximum' (x:xs)では、ガードを用いて条件分岐している。
<br>
条件分岐１　maxTailが先頭要素xよりも大きい場合、maxTailをxとする。
<br>
条件分岐2　その他のmaxTailがx以上の値をとる場合は、そのままmaxTailになる。
whereで変数宣言をし、xを除いたリストの要素の中で一番大きな値になる変数maxTailを定義している。

```haskell:maximun'.hs
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
haskellでは、if文でたくさん分岐しなくても、パターンマッチを使えばスッキリかける。
次に、maxを使って、maximumを書き換える。
```
ghci> max 1 10
10
ghci> max 200 1
200
```

```haskell:maximun'.hs
maximum' :: (Ord a) => [a] -> a  
maximum' [] = error "maximum of empty list"  
maximum' [x] = x  
maximum' (x:xs) = max x (maximum' xs)  
```




