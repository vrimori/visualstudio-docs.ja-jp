---
title: 匿名メソッドとコード分析 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced736f74be4216a069b27aed096989a89cf518d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名メソッドとコード分析
*匿名メソッド*メソッド名を持っていないです。 匿名メソッドは、コード ブロックをデリゲートのパラメーターとして渡すを最も頻繁に使用されます。  
  
 このトピックでは、コード分析で警告と匿名メソッドに関連付けられているメトリックを処理する方法について説明します。  
  
## <a name="anonymous-methods-declared-in-a-member"></a>メンバーで宣言された匿名メソッド  
 警告と匿名メソッドのメソッドまたはアクセサーなどのメンバーで宣言されているメトリックは、メソッドを宣言するメンバーに関連付けられます。 メソッドを呼び出すメンバーに関連付けられていません。  
  
 たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod**に対して発生する必要がある**Method1**および not **Method2**です。  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
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
 警告およびフィールドへの代入をインラインとして宣言されている匿名メソッドのメトリックは、コンス トラクターに関連付けられます。 フィールドとして宣言されている場合`static`(`Shared`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、警告およびメトリックは、それ以外のクラスのコンス トラクターに関連付け、インスタンス コンス トラクターに関連付けられています。  
  
 たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod1**の暗黙的に生成された既定のコンス トラクターに対してが生成されます**クラス**です。 一方で見つかったもの**anonymousMethod2**暗黙的に生成されたクラスのコンス トラクターに対して適用されます。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
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
  
 クラスには、複数のコンス トラクターを持つフィールドに値を代入するインラインの匿名メソッドが含まれます。 この場合、警告とメトリックが関連付けられますコンス トラクターをすべて同じクラス内の別のコンス トラクターがコンス トラクターのチェーンしない限り、します。  
  
 たとえば、次のクラスの宣言内にあるすべての警告で**anonymousMethod**に対して発生する必要がある**Class(int)**と**class (string)**が、に対してではなく**Class()**です。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
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
  
 これは、予期しない見える可能性があります、これは、コンパイラは別のコンス トラクターをチェーンしていないすべてのコンス トラクターに一意のメソッドを出力です。 この動作のための違反で発生**anonymousMethod**とは別に抑制する必要があります。 つまり場合は、新しいコンス トラクターは、導入された、警告を抑制していたを**Class(int)**と**class (string)**新しいコンス トラクターに対しても抑制する必要があります。  
  
 2 つの方法でこの問題を回避することができます。 宣言すること**anonymousMethod**で共通のコンス トラクターをすべてのコンス トラクター チェーン。 または、すべてのコンス トラクターによって呼び出される初期化メソッドで宣言する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)