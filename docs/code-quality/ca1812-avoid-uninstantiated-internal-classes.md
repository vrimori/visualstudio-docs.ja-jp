---
title: 'CA1812: インスタンス化されていない内部クラスを使用しないでください'
ms.date: 11/04/2016
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
ms.openlocfilehash: cf39d775c5602aaddf5b9487d175ddbbdd70d52e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
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
 このルールが、型のコンス トラクターのいずれかの呼び出しを特定するし、呼び出しが存在しない場合は、違反を報告します。

 次の種類は、この規則ではチェックされません。

-   値型

-   抽象型

-   列挙

-   デリゲート

-   コンパイラによって生成された配列型

-   型をインスタンス化することはできず、定義する`static`(`Shared` Visual Basic で) メソッドにのみです。

 適用する場合<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>は、分析する、アセンブリをこの規則は発生しませんとマークされているコンス トラクターで`internal`別フィールドが使用されているかどうかがわからないため`friend`アセンブリ。

 場合でも、この制限を回避することはできません[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コード分析、外部のスタンドアロン FxCop は場合に発生する内部コンス トラクターすべて`friend`分析のアセンブリが存在します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、型を削除またはそれを使用するコードを追加します。 型に静的メソッドのみが含まれている場合をコンパイラが既定のパブリック インスタンス コンス トラクターを生成するを防ぐために、型を次のいずれかを追加します。

-   プライベート コンス トラクター型を対象とする[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]version 1.0 および 1.1 です。

-   `static` (`Shared` Visual basic) 修飾子の種類を対象とする[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。 次の状況では、この警告を抑制することをお勧めします。

-   など、クラスが遅延バインディングされたリフレクション メソッドによって作成された<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>です。

-   クラスは、ランタイムによって自動的に作成または[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]です。 たとえば、クラスを実装する<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>または<xref:System.Web.IHttpHandler?displayProperty=fullName>です。

-   クラスは、新しい制約を持つジェネリック型パラメーターとして渡されます。 たとえば、次の例では、このルールが発生します。

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

## <a name="related-rules"></a>関連規則
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)