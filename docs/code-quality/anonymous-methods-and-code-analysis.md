---
title: "匿名メソッドとコード分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "匿名メソッド, コード分析"
  - "コード分析, 匿名メソッド"
  - "メソッド, 匿名"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名メソッドとコード分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*匿名メソッド*は、名前を持たないメソッドです。  匿名メソッドは、コード ブロックをデリゲート パラメーターとして渡すために最も頻繁に使用されます。  
  
 このトピックでは、匿名メソッドに関連付けられた警告やメトリックスがコード分析でどのように処理されるかについて説明します。  
  
## メンバー内で宣言された匿名メソッド  
 メソッドやアクセサーなど、メンバーで宣言されている匿名メソッドの警告やメトリックスは、メソッドを宣言するメンバーに関連付けられます。  メソッドを呼び出すメンバーには関連付けられません。  
  
 たとえば、次のクラスでは、**anonymousMethod** の宣言内にあるすべての警告は、**Method2** ではなく **Method1** に対して発生させる必要があります。  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
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
  
## インラインの匿名メソッド  
 フィールドへのインラインの代入として宣言された匿名メソッドの警告やメトリックスは、コンストラクターに関連付けられます。  フィールドが `static` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 内の `Shared`\) として宣言されている場合、警告とメトリックスはクラス コンストラクターに関連付けらます。それ以外の場合は、インスタンス コンストラクターに関連付けられます。  
  
 たとえば、次のクラスでは、**anonymousMethod1** の宣言内にあるすべての警告は、暗黙的に生成された **Class** の既定のコンストラクターに対して発生します。  一方、**anonymousMethod2** 内にある警告は、暗黙的に生成されたクラス コンストラクターに対して適用されます。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
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
  
 クラスには、複数のコンストラクターを持つフィールドに値を割り当てる、インラインの匿名メソッドが含まれることがあります。  この場合、そのコンストラクターが同じクラスの別のコンストラクターにチェーンしている限り、警告とメトリックスはすべてのコンストラクターに関連付けられます。  
  
 たとえば、次のクラスでは、**anonymousMethod** の宣言内にあるすべての警告は、**Class\(int\)** および **Class\(string\)** に対して発生させる必要がありますが、**Class\(\)** に対して発生させる必要はありません。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
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
  
 予想外に思えるかもしれませんが、これは、コンパイラが別のコンストラクターにチェーンしていないすべてのコンストラクターに一意のメソッドを出力するために発生します。  この動作のため、**anonymousMethod** 内で発生するすべての違反は個別に抑制する必要があります。  また、新しいコンストラクターが導入された場合は、それまで **Class\(int\)** と **Class\(string\)** に対して抑制していた警告を、新しいコンストラクターに対しても抑制する必要があります。  
  
 この問題は、2 つの方法のいずれかで回避することができます。  すべてのコンストラクターにチェーンしている共通のコンストラクター内に **anonymousMethod** を宣言します。  または、すべてのコンストラクターから呼び出される初期化メソッド内に宣言します。  
  
## 参照  
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)