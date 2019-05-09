## Syntax in Functions

Preludeからたいわモードに変えたい
```
set prompt "ghci> "
```

たーみなるで::をつかいたいとき

```
:{
関数の型宣言::が使える
:}
```

### ぱたーんまっち

関数定義では、それぞれのパターンに対して関数の中身を定義することができる。
数、文字、リスト、タプルなどの様々な型をパターンマッチで使うことができる。

例)７かどうかを判定するlucky関数
lucky関数を呼び出すと、パターンの上から下までを確認していき、入力がパターンと適応した場合は、一致した関数の内容が使用される。

```
:{
lucky :: (Integral a) => a -> String  
lucky 7 = "LUCKY NUMBER SEVEN!"  
lucky x = "Sorry, you're out of luck, pal!" 
:}
ghci> lucky 7
"LUCKY NUMBER SEVEN!"
ghci> lucky 3
"Sorry, you're out of luck, pal!"
```

例2) sayMe関数
1から5までの数字に対し、英語での出力をし、それ以外の数字では"Not between 1 and 5"と出力する関数
```
:{
sayMe :: (Integral a) => a -> String  
sayMe 1 = "One!"  
sayMe 2 = "Two!"  
sayMe 3 = "Three!"  
sayMe 4 = "Four!"  
sayMe 5 = "Five!"  
sayMe x = "Not between 1 and 5"  
:}
```

階乗関数
前章で書いた階乗関数

リスト関数productを使って書いた階乗関数
product:数のリストの積を返す

```
:{
factorial :: Integer -> Integer  
factorial n = product [1..n]  
:}
```

再帰を使用
入力した数の一つ前の数字と掛け合わせて書いた階乗関数

```
:{
factorial :: (Integral a) => a -> a  
factorial 0 = 1  
factorial n = n * factorial (n - 1) 
:}
```

パターンマッチの失敗例

全てのパターンを含んだ関数でない場合、エラーが出て、パターンマッチが失敗する。
charName関数では、全てのアルファベットに対応していないため、関数のbody内で記述していない入力をされると、"関数charName内でその様なパターンは存在しない"とエラーが出てしまう。
```
:{
charName :: Char -> String  
charName 'a' = "Albert"  
charName 'b' = "Broseph"  
charName 'c' = "Cecil" 
:}
ghci> charName 'a'  
"Albert"  
ghci> charName 'b'  
"Broseph"  
ghci> charName 'h'  
"*** Exception: tut.hs:(53,0)-(55,21): Non-exhaustive patterns in function charName  
```

タプルもパターンマッチで使える。

```
:{
addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)  
addVectors a b = (fst a + fst b, snd a + snd b)  
:}
```





