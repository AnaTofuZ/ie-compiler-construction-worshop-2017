LLVM

以下のCのSource codewがコンパイラによってどう変換されるかを調べる

``` C
    extern int printf(char *,...);
    #define TYPE int
    TYPE f(TYPE a, TYPE b) {
        return a + b;
    }
    int main() 
    {
        TYPE a = 1;
        TYPE b = 2;
        printf("%x = %x + %x \n",f(a,b),a,b);
        return 0;
    }
```

---

# (1) cpp

- `clang -E` での出力を調べる

- 変換されている部分はどこか。 printf を protoptype ではなく #include <stdio.h> で定義した時はどうなるか。

## 解説

clangの `-E` オプションはmanによると `-E     Run the preprocessor stage.`

つまりプリプロセッサまで処理を行う。
普通のコンパイルの時はあくまで内部的に行われている。


(参考:[プリプロセッサ](http://itref.fc2web.com/c/preprocessor.html))
