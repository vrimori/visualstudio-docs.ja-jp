---
title: ': Ca 1812 インスタンス化されていない内部クラス |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f294126c013b8fc656bf4f08dec17755a657b12
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589953"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: インスタンス化されていない内部クラスを使用しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1812: インスタンス化されていない内部クラスを避けるため](https://docs.microsoft.com/visualstudio/code-quality/ca1812-avoid-uninstantiated-internal-classes)します。

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

-   値型

-   抽象型

-   列挙

-   デリゲート

-   コンパイラによって生成された配列型

-   型をインスタンス化することはできず、定義する`static`(`Shared` Visual Basic で) メソッドのみです。

 適用した場合<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>は分析されて、アセンブリをこのルールがないとマークされているすべてのコンス トラクターでトリガー`internal`別フィールドが使用されているかどうかを見分けることはできませんので`friend`アセンブリ。

 この制限を回避できない場合でも[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]コード分析、外部のスタンドアロン FxCop は場合に発生する内部コンス トラクターですべて`friend`アセンブリが、分析に存在します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、型を削除またはそれを使用するコードを追加します。 型に静的メソッドのみが含まれている場合は、コンパイラが既定のパブリック インスタンス コンス トラクターを生成するを防ぐために、型に、次のいずれかを追加します。

-   プライベート コンス トラクター型を対象とする[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]version 1.0 および 1.1。

-   `static` (`Shared` Visual basic) 修飾子は型を対象とする[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制しても安全です。 次の状況では、この警告を抑制することをお勧めします。

-   などクラスが遅延バインディング リフレクション メソッドによって作成された<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>します。

-   クラスは、ランタイムによって自動的に作成または[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]します。 たとえば、実装するクラスの<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>または<xref:System.Web.IHttpHandler?displayProperty=fullName>します。

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



