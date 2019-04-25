素数判定

```
-- 一行目で、入力をInt型にして、出力をBool型に変換する
isPrime :: Int -> Bool　

{-
以下では、ガードを使っている
ガードとは、
式
  | 条件1 = 条件1にマッチしたとの処理
  | 条件2 = 条件2にマッチしたとの処理
  | otherwise = いずれの条件にもマッチしなかった時の処理
素数とは、１と自分自身以外に以外に約数を持たない数
2,3,5,7,11...
なので、
2は素数である
0,1は素数ではない
偶数は素数ではない
その他はwari関数にて、再帰処理を使って確認している
-}

isPrime 2 = True
isPrime n
    | n < 2            = False
    | (n `mod` 2) == 0 = False
    | otherwise        = wari 3 n
{-
wari関数を新たに定義する
if 条件式 then 式1 else 式2

-}
wari :: Int -> Int -> Bool
wari i n = if i * i <= n
            then (if n `mod` i == 0
                    then False
                    else wari (i + 2) n)
            else True
            
```
