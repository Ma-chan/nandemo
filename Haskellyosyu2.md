# An intro to lists

- ハスケルでは、リストは同種データ構造
  - 同じ型のいくつかの要素が保存できる
- GHCIでは名前を定義するために、letを使う
  - (例)let a=1とa=1はGHCI上で同じ意味である
  
- リストの定義
```
ghci> let lostNumbers = [4,8,15,16,23,42]  
ghci> lostNumbers  
[4,8,15,16,23,42]  
```

- 文字列はリストなので、リスト関数を使用することが出来る
 - "hello"は['h'、 'e'、 'l'、 'l'、 'o']を省略した糖衣構文のリスト

- リスト同士は++で繋げることが出来る
```
ghci> [1,2,3,4] ++ [9,10,11,12]  
[1,2,3,4,9,10,11,12]  
ghci> "hello" ++ " " ++ "world"  
"hello world"  
ghci> ['w','o'] ++ ['o','t']  
"woot"  
```

- : で文字列同士または数字とリストを繋げることが出来る
  - 
```
ghci> 'A':" SMALL CAT"  
"A SMALL CAT"  
ghci> 5:[1,2,3,4,5]  
[5,1,2,3,4,5]  
```














