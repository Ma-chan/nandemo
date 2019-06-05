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
その他の合成数はwari関数にて、再帰処理を使って確認している
-}

isPrime 2 = True
isPrime n
    | n < 2            = False
    | (n `mod` 2) == 0 = False
    | otherwise        = wari 3 n
{-
wari関数を新たに定義する
if 条件式 then 式1 else 式2
試し割りはiの平方根以下の値のみの確認で良い
合成数の場合、元の数の平方数以下で割り切れない場合、約数は出てこないため、素数と判定できる
平方数以上の値を調べても、対となる片割れがないと、約数は出てこないので、素数と判定できる
例)n=16(合成数)
[1,2,4,8,16]
約数には、掛け合わせると、元の数になる組み合わせが存在する
1*16
2*8
4*4
-}
wari :: Int -> Int -> Bool
wari i n = if i * i <= n
            then (if n `mod` i == 0
                    then False
                    else wari (i + 2) n)
            else True
            
```


<img src="https://maigo-pet.net/tokusyuu/img/dog-maigo-4.jpg" width="100px" height="100px">
