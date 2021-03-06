# Python学习之路-异常


## 简介

程序在运行时，如果 `Python 解释器` 遇到到一个错误，会停止程序的执行，并且提示一些错误信息，这就是异常。程序停止执行并且提示错误信息这个动作，我们通常称之为：抛出(raise)异常。

程序开发时，很难将所有的特殊情况都处理的面面俱到，通过异常捕获可以针对突发事件做集中的处理，从而保证程序的稳定性和健壮性。

## 捕获异常

在程序开发中，如果对某些代码的执行不能确定是否正确，可以增加 `try(尝试)` 来捕获异常。

捕获异常最简单的语法格式：

```python
try:
    尝试执行的代码
except:
    出现错误的处理
```

- `try`尝试，下方编写要尝试代码，不确定是否能够正常执行的代码
- `except`如果不是，下方编写尝试失败的代码

## 错误类型捕获

在程序执行时，可能会遇到不同类型的异常，并且需要针对不同类型的异常，做出不同的响应，这个时候，就需要捕获错误类型了

语法如下：

```python
try:
    # 尝试执行的代码
    pass
except 错误类型1:
    # 针对错误类型1，对应的代码处理
    pass
except (错误类型2, 错误类型3):
    # 针对错误类型2 和 3，对应的代码处理
    pass
except Exception as result:
    print("未知错误 %s" % result)
```

当 `Python` 解释器抛出异常时，最后一行错误信息的第一个单词，就是错误类型。

## 捕获未知错误

在开发时，要预判到所有可能出现的错误，还是有一定难度的，如果希望程序无论出现任何错误，都不会因为 `Python` 解释器抛出异常而被终止，可以再增加一个`except`。

语法如下：

```python
except Exception as result:
    print("未知错误 %s" % result)
```

## 异常捕获完整语法

在实际开发中，为了能够处理复杂的异常情况，完整的异常语法如下：

```python
try:
    # 尝试执行的代码
    pass
except 错误类型1:
    # 针对错误类型1，对应的代码处理
    pass
except 错误类型2:
    # 针对错误类型2，对应的代码处理
    pass
except (错误类型3, 错误类型4):
    # 针对错误类型3 和 4，对应的代码处理
    pass
except Exception as result:
    # 打印错误信息
    print(result)
else:
    # 没有异常才会执行的代码
    pass
finally:
    # 无论是否有异常，都会执行的代码
    print("无论是否有异常，都会执行的代码")
```

{{< admonition tip "补充" true >}}

`else`：只有在没有异常时才会执行的代码。`finally`：无论是否有异常，都会执行的代码

{{< /admonition >}}

## 异常的传递

当函数/方法执行出现异常，会将异常传递给函数/方法的调用一方。如果传递到主程序，仍然没有异常处理，程序才会被终止。

{{< admonition tip "提示" true >}}

在开发中，可以在主函数中增加异常捕获，而在主函数中调用的其他函数，只要出现异常，都会传递到主函数的异常捕获中，这样就不需要在代码中，增加大量的异常捕获，能够保证代码的整洁。

{{< /admonition >}}

## 抛出 `raise` 异常

除了代码执行出错 `Python` 解释器会抛出异常之外，还可以根据应用程序特有的业务需求主动抛出异常。`Python` 中提供了一个 `Exception`异常类。在开发时，如果满足特定业务需求时希望抛出异常，可以：创建一个 `Exception` 的对象，使用 `raise` 关键字抛出 异常对象。
