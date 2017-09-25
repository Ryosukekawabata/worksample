# lambdaについて
lambdaとは「匿名関数（無名な関数）」のことです。
関数を生成し実行、引数で渡して戻り値として受け取ることができます。

## Procとの違い

両方ともブロックをオブジェクトにしたものですが、「return」と「引数」の違いがあります。

### returnの違い

Procの場合は
def double
  p = Proc.new{ return 10 }
  result = p.call
  return result * 2
end

another_double

ProcからでなくProcが定義されたスコープから戻ります

lambdaの場合は
def double(callable_object)
  callble_object.call * 2
end
a_lambda = lambda{ return 10 }
double(a_lambda)

そのままlambdaに戻ります

### 引数の違い

Procの場合は
p = Proc.new{ |a, b| [a, b] }
p.call(1, 2, 3)
p.call(1)

元で定義した引数の数に合わせて返します。

lambdaの場合はArugumentErrorになります。

##まとめ
lambdaは引数の数を文法チェックしています。
そのため、呼び出す時に引数の数が違うと前述通りArugumentErrorになります。
Procは引数に値の指定がなかった場合、nilが引数に代入されます。
