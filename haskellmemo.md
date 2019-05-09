## Syntax in Functions
### Reference

Preludeからたいわモードに変えたい
```
set prompt "ghci> "
```
### 関数の実行

ターミナルで実行したい時
```
:{
関数の型宣言::が使える
:}
```
ファイル保存からの実行

```
:load ファイル名.hs
:l ファイル名.hs
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

### 再帰

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
パターンを定義する時に、はじめに具体的な0!=1の様なパターンを書いてから、一般的なn!=n*(n-1)を書いた方が良い

```
:{
factorial :: (Integral a) => a -> a  
factorial 0 = 1  
factorial n = n * factorial (n - 1) 
:}
```

パターンマッチの失敗例

全てのパターンを含んだ関数でない場合、エラーが出て、パターンマッチが失敗する。
charName関数では、パターンマッチで考慮されていない場合はエラーになってしまう。
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
そのおかげで、二次元領域で(x1,y1),(x2,y2)の様な二つのベクトルの中身同士の計算ができる。
(a,a)->(a,a)->(a,a)では、二つのタプルの入力をして、一つのタプルを出力する、という関数の変数の宣言をしている。

```
:{
addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)  
addVectors a b = (fst a + fst b, snd a + snd b)  
:}
```

パターンマッチを使って書いたaddVector関数


```
:{
addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)  
addVectors (x1, y1) (x2, y2) = (x1 + x2, y1 + y2)
:}
```


```
:{
first :: (a, b, c) -> a  
first (x, _, _) = x  
  
second :: (a, b, c) -> b  
second (_, y, _) = y  
  
third :: (a, b, c) -> c  
third (_, _, z) = z  
:}
```
タプルを操作するfstとsndの変数を3つにしたfstとsndを作る
_はその要素をスキップすることと同じ意味。

```
:{
first :: (a, b, c) -> a  
first (x, _, _) = x  
  
second :: (a, b, c) -> b  
second (_, y, _) = y  
  
third :: (a, b, c) -> c  
third (_, _, z) = z  
:}
```
リスト関数headをパターンマッチで実装する場合、
Remind 
head:リストの先頭要素を返すリスト関数

```
head' :: [a] -> a  
head' [] = error "Can't call head on an empty list, dummy!"  
head' (x:_) = x  
```

tell関数では、(x:[])は糖衣構文の[x]と同じ意味、(x:y:[])は[x,y]と同じ意味、2つ以上のリストでは、[]が使えないので、_でリストの要素数が2つ以上の場合について書いている。

```
tell :: (Show a) => [a] -> String  
tell [] = "The list is empty"  
tell (x:[]) = "The list has one element: " ++ show x  
tell (x:y:[]) = "The list has two elements: " ++ show x ++ " and " ++ show y  
tell (x:y:_) = "This list is long. The first two elements are: " ++ show x ++ " and " ++ show y  
```

リスト関数lengthを再帰とパターンマッチを使って、実装する。

```
length' :: (Num b) => [a] -> b  
length' [] = 0  
length' (_:xs) = 1 + length' xs 
```

sum関数を再帰とパターンマッチを使って実装する。

```
sum' :: (Num a) => [a] -> a  
sum' [] = 0  
sum' (x:xs) = x + sum' xs  
```

### ガード



輪講終了時
対話モードを抜ける時

```
:quit
:q
```


