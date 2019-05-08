## はすける

### ぱたーんまっち

関数定義では、それぞれのパターンに対して関数の中身を定義することができる。
数、文字、リスト、タプルなどの様々な型をパターンマッチで使うことができる。

例)７かどうかを判定するlucky関数
```
lucky :: (Integral a) => a -> String  
lucky 7 = "LUCKY NUMBER SEVEN!"  
lucky x = "Sorry, you're out of luck, pal!" 
```

