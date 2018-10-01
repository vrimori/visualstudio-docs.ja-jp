---
title: 'CA1062: パブリック メソッドの引数の検証'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5be9d4e0e251d0e84627b04ccdd5bd4842d2a0e8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546864"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: パブリック メソッドの引数の検証

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

その引数は、かどうかを確認せず、外部から参照できるメソッドを逆参照引数のいずれかの`null`(`Nothing` Visual Basic で)。

## <a name="rule-description"></a>規則の説明

外部から参照可能なメソッドに渡されるすべての参照引数を照合する`null`します。 必要に応じて、スロー、<xref:System.ArgumentNullException>ときに、引数が`null`。

メソッドは、public または protected に宣言されているために、不明なアセンブリから呼び出すことが、メソッドのすべてのパラメーターを検証する必要があります。 内部メソッドを作成および適用する必要がある既知のアセンブリによってのみ呼び出されるメソッドの場合、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>メソッドを含むアセンブリへの属性します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、各参照引数を検証`null`です。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

関数のもう 1 つのメソッド呼び出しによって逆参照されるパラメーターが検証済みであることを確認する場合は、この規則による警告を抑制できます。

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

コピー コンス トラクターがフィールドまたは参照オブジェクトのプロパティを設定するには、ca 1062 ルール違反もことができます。 コピーされたオブジェクトのコピー コンス トラクターに渡される可能性があるために、違反が発生する`null`(`Nothing` Visual Basic で)。 違反を解決するには、static (Visual Basic では Shared) メソッドを使用して、コピーされたオブジェクトが null でないことを確認します。

次の`Person`クラスなど、`other`オブジェクトに渡される、`Person`コピー コンス トラクターがあります`null`します。

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

次のように改訂された`Person`など、`other`コピー コンス トラクターに渡されるオブジェクトが最初にチェックで null を`PassThroughNonNull`メソッド。

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