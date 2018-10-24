---
title: 'CA1812: インスタンス化されていない内部クラスを使用しないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45ff6e07abb77623fe1007ef5e13556e26852224
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827465"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: インスタンス化されていない内部クラスを使用しないでください

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

アセンブリ レベルの型のインスタンスが、アセンブリ内のコードから作成されません。

## <a name="rule-description"></a>規則の説明

このルールは、型のコンス トラクターの 1 つの呼び出しの検索を試み、呼び出しが検出されない場合は、違反を報告します。

次の種類は、このルールではチェックされません。

- 値型

- 抽象型

- 列挙

- デリゲート

- コンパイラによって生成された配列型

- 型をインスタンス化することはできず、定義する`static`(`Shared` Visual Basic で) メソッドのみです。

適用した場合<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>は分析されて、アセンブリをこのルールがないとマークされているすべてのコンス トラクターでトリガー`internal`別フィールドが使用されているかどうかを見分けることはできませんので`friend`アセンブリ。

場合でも、Visual Studio コード分析でのこの制限を回避することはできません、外部のスタンドアロン FxCop は場合は、すべて内部コンス トラクターに発生する`friend`アセンブリが、分析に存在します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、型を削除またはそれを使用するコードを追加します。 型に静的メソッドのみが含まれている場合は、コンパイラが既定のパブリック インスタンス コンス トラクターを生成するを防ぐために、型に、次のいずれかを追加します。

- .NET Framework version 1.0 および 1.1 を対象とする型のプライベート コンス トラクターです。

- `static` (`Shared` Visual basic) 修飾子は型を対象とする[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

このルールから警告を抑制しても安全です。 次の状況では、この警告を抑制することをお勧めします。

- などクラスが遅延バインディング リフレクション メソッドによって作成された<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>します。

- クラスは、ランタイムによって自動的に作成または[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]します。 たとえば、実装するクラスの<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>または<xref:System.Web.IHttpHandler?displayProperty=fullName>します。

- クラスは、新しい制約を持つジェネリック型パラメーターとして渡されます。 たとえば、次の例では、このルールが発生します。

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  このような場合は、この警告を抑制することをお勧めします。

## <a name="related-rules"></a>関連するルール

[CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)