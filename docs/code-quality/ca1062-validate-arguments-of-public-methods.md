---
title: "Ca 1062: パブリック メソッドの引数の検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f225159e551dac2327c35774db846eec4ccc6fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: パブリック メソッドの引数の検証
|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 外部から参照できるメソッドを逆参照の参照引数のいずれかの引数がかどうかを確認せず`null`(`Nothing` Visual Basic で)。  
  
## <a name="rule-description"></a>規則の説明  
 外部から参照可能なメソッドに渡されるすべての参照引数を照合する基準として`null`です。 必要に応じて、スロー、<xref:System.ArgumentNullException>ときに、引数が`null`です。  
  
 メソッドは、public または protected が宣言されているために、不明なアセンブリから呼び出すことが、メソッドのすべてのパラメーターを検証する必要があります。 ように、メソッドの内部を適用する場合は、メソッドは、既知のアセンブリによってのみ呼び出される設計されていますが、必要があります、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>メソッドが含まれているアセンブリに属性します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、各参照引数を検証`null`です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 逆参照されるパラメーターが関数内の別のメソッド呼び出しによって検証されたことを確認する場合は、この規則による警告を抑制できます。  
  
## <a name="example"></a>例  
 次の例では、規則に違反するメソッドと、規則に適合するメソッドを示します。  
  
 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```
  
## <a name="example"></a>例  
 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]、このルールでは、検証を別のメソッドにパラメーターが渡されていることが検出されません。  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
```

## <a name="example"></a>例  
 コピー コンス トラクターがフィールドまたは参照オブジェクトのプロパティを設定するには、ca 1062 ルール違反もことができます。 コピーされるオブジェクトのコピー コンス トラクターに渡される可能性があるために、違反が発生する`null`(`Nothing` Visual Basic で)。 違反を解決するには、静的 (Visual Basic では Shared) メソッドを使用して、コピーされたオブジェクトが null でないことを確認します。  
  
 次に`Person`クラスなど、`other`に渡されるオブジェクト、`Person`コピー コンス トラクターがあります`null`です。  
  
```csharp  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
```
  
## <a name="example"></a>例  
 次に改訂`Person`例では、`other`コピー コンス トラクターに渡されるオブジェクトが最初にチェックで null を`PassThroughNonNull`メソッドです。  
  
```csharp  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```