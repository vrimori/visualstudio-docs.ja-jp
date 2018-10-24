---
title: 'Ca 1062: パブリック メソッドの引数の検証 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7d5b5039c08e27dd97c0119948c87d7295756d7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811985"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: パブリック メソッドの引数の検証
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 関数のもう 1 つのメソッド呼び出しによって逆参照されるパラメーターが検証済みであることを確認する場合は、この規則による警告を抑制できます。

## <a name="example"></a>例
 次の例では、規則に違反するメソッドと、規則に適合するメソッドを示します。

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>例
 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]、このルールでは、パラメーターが検証を行う別のメソッドに渡されることは検出されません。

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>例
 コピー コンス トラクターがフィールドまたは参照オブジェクトのプロパティを設定するには、ca 1062 ルール違反もことができます。 コピーされたオブジェクトのコピー コンス トラクターに渡される可能性があるために、違反が発生する`null`(`Nothing` Visual Basic で)。 違反を解決するには、static (Visual Basic では Shared) メソッドを使用して、コピーされたオブジェクトが null でないことを確認します。

 次の`Person`クラスなど、`other`オブジェクトに渡される、`Person`コピー コンス トラクターがあります`null`します。

```

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

```
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



