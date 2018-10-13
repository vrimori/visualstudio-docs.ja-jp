---
title: 'Ca 2122: リンク確認要求でメソッドを間接的に公開しないでしないで |Microsoft Docs'
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
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b149b6e2688169a368461c2afbc371f138c39dd9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295756"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: リンク確認要求で間接的にメソッドを公開しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクト メンバーが、[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)と、セキュリティ チェックを実行しないメンバーによって呼び出されます。

## <a name="rule-description"></a>規則の説明
 リンク確認要求では、直接の呼び出し元のアクセス許可しかチェックされません。 場合、メンバー`X`セキュリティ要求呼び出しコード要求によって保護された、リンク、呼び出し元、必要な権限を使用せず、呼び出し元の責任も負わない`X`プロテクト メンバーにアクセスします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 セキュリティ[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)またはメンバーへのオンデマンドのリンクを不要になったリンク確認要求で保護されたメンバーをセキュリティ保護されていないアクセスを提供するようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を安全に抑制するのには操作または破壊的な方法で使用できるリソースへのアクセスを呼び出し元に付与しないようにを確認する必要があります。

## <a name="example"></a>例
 次の例では、ライブラリの規則に違反して、ライブラリの脆弱性を示すアプリケーションを示します。 サンプル ライブラリは、まとめてルールに違反している 2 つのメソッドを提供します。 `EnvironmentSetting`メソッドは、環境変数への無制限アクセスのリンク確認要求によってセキュリティで保護されます。 `DomainInformation`メソッドには、呼び出し元のセキュリティ確認要求、なしを呼び出す前に`EnvironmentSetting`します。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>例
 次のアプリケーションでは、セキュリティ保護されていないライブラリ メンバーを呼び出します。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **セキュリティ保護されていないメンバーからの値: seattle.corp.contoso.com**
## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



