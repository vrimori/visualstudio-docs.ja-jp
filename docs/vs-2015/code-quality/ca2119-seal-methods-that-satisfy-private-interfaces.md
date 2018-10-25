---
title: '2119: プライベート インターフェイスを満たすメソッドをシール |Microsoft Docs'
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
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c6d3e102cde1fc010f777006d629fa2d19add894
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825397"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: プライベート インターフェイスを満たすメソッドをシールします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 継承可能なパブリック型のオーバーライド可能なメソッド実装を提供する、 `internal` (`Friend` Visual Basic で) インターフェイス。

## <a name="rule-description"></a>規則の説明
 インターフェイス メソッドがあるパブリック アクセシビリティは、実装する型を変更できません。 内部のインターフェイスは、インターフェイスを定義するアセンブリの外側に実装されるものではありませんが、コントラクトを作成します。 使用して、内部のインターフェイスのメソッドを実装するパブリック型、 `virtual` (`Overridable` Visual basic) 修飾子は、アセンブリ外にある派生型でオーバーライドされるメソッドを使用します。 2 番目の型定義のアセンブリでは、メソッドを呼び出し、内部専用の契約が必要ですが場合、代わりに、外部のアセンブリでオーバーライドされたメソッドが実行されるときに、動作が漏えいする可能性があります。 これには、セキュリティの脆弱性が作成されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、メソッドが、次のいずれかを使用して、アセンブリの外部にオーバーライドされないように。

-   宣言する型`sealed`(`NotInheritable` Visual Basic で)。

-   宣言する型のアクセシビリティを変更する`internal`(`Friend` Visual Basic で)。

-   すべてのパブリック コンス トラクターを宣言する型から削除します。

-   メソッドの実装を使用せず、`virtual`修飾子。

-   メソッドを明示的に実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告を抑制するには、安全ではルールの場合、セキュリティの問題が存在しないことを注意深くレビューは、アセンブリの外部メソッドがオーバーライドされた場合に悪用可能な場合があります。

## <a name="example"></a>例
 次の例は、型`BaseImplementation`、この規則に違反します。

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>例
 次の例では、前の例の仮想メソッドの実装を悪用します。

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>関連項目
 [インターフェイス](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)[インターフェイス](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)



