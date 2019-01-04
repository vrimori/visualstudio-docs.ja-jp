---
title: 匿名メソッドのコード分析の警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47f90e0a9ca01e76ea1a3686c790dcf00a4becde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860781"
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名メソッドとコード分析

*匿名メソッド*は名前を持たないメソッドです。 匿名メソッドは、コード ブロックをデリゲート パラメーターとして渡すを最も頻繁に使用されます。 この記事では、コード分析での警告と匿名メソッドのメトリックを処理する方法について説明します。

## <a name="anonymous-methods-declared-in-a-member"></a>メンバーで宣言された匿名メソッド

警告と匿名メソッドまたはアクセサーなどのメンバーで宣言されているメソッドのメトリックは、メソッドを宣言するメンバーに関連付けられます。 メソッドを呼び出すメンバーに関連付けられていません。

たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod**に対して発生する必要がある**Method1**なく**Method2**します。

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>インラインの匿名メソッド

警告と、フィールドへの代入をインラインとして宣言されている匿名メソッドのメトリックは、コンス トラクターに関連付けられます。 フィールドとして宣言されている場合`static`(`Shared` Visual Basic で)、警告とメトリックは、クラス コンス トラクターに関連付けられます。 それ以外の場合、インスタンス コンス トラクターに関連付けられています。

たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod1**の暗黙的に生成される既定のコンス トラクターで**クラス**します。 内にある警告**anonymousMethod2**暗黙的に生成されたクラスのコンス トラクターに適用されます。

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

クラスには、複数のコンス トラクターを持つフィールドに値を代入するインラインの匿名メソッドが含まれます。 ここでは、警告とメトリックをすべてのコンス トラクターに関連付けられていない限り、そのコンス トラクターは、同じクラスの別のコンス トラクターにチェーンします。

たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod**に対して発生する必要がある**Class(int)** と**class (string)** が、に対してではなく**Class()** します。

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

コンパイラは、別のコンス トラクターにチェーンされていないすべてのコンス トラクターに一意のメソッドを出力するので、コンス トラクターに対して、警告が発生します。 この動作のための違反が発生するで**anonymousMethod**とは別に抑制する必要があります。 つまり、新しいコンス トラクターがある場合、導入された警告**Class(int)** と**class (string)** 新しいコンス トラクターに対しても抑制する必要があります。

2 つの方法のいずれかでこの問題を回避することができます。

- 宣言**anonymousMethod**で共通のコンス トラクターをすべてのコンス トラクター チェーン。
- 宣言**anonymousMethod**ですべてのコンス トラクターによって呼び出される初期化メソッドです。

## <a name="see-also"></a>関連項目

- [マネージド コードの品質の分析](../code-quality/code-analysis-for-managed-code-overview.md)