---
title: 'Ca 2108: 値型で宣言型のセキュリティの確認 |Microsoft Docs'
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
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 49159696edd713c85a44e48ee0e79ccd5acf2753
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284584"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: 値型での宣言セキュリティをレビューします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクトの値の型がによってセキュリティ保護、[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)または[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)します。

## <a name="rule-description"></a>規則の説明
 値の型に割り当てられ他のコンス トラクターの実行前に既定のコンス トラクターによって初期化します。 値の型が Demand または LinkDemand によってセキュリティ保護されていて、呼び出し元には、以外の任意のコンス トラクター、セキュリティ チェックに適合するアクセス許可がありません。 既定値は失敗すると、およびセキュリティ例外がスローされます。 値の型の割り当ては解除されません。既定のコンス トラクターによって設定された状態で中断するとします。 値型のインスタンスを渡す呼び出し元が作成またはインスタンスにアクセスする権限を持っているとは限りません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 種類、セキュリティ チェックを削除して、その場所に使用してメソッド レベルのセキュリティを確認しますしない限り、この規則違反を修正することはできません。 この方法で、違反を修正できなくなるから値型のインスタンスを取得する不適切なアクセス許可を持つ呼び出し元に注意してください。 既定の状態で、値型のインスタンスは、機密情報を公開しないと、有害な方法では使用できませんをことを確認する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 呼び出し元は、既定の状態にある値型のインスタンスを取得するセキュリティの脅威がない場合は、この規則による警告を抑制できます。

## <a name="example"></a>例
 次の例では、この規則に違反する値の型を含むライブラリを示します。 なお、`StructureManager`型では、値型のインスタンスを渡す呼び出し元が作成またはインスタンスにアクセスする権限を持っている前提としています。

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>例
 次のアプリケーションでは、ライブラリの脆弱性を示しています。

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **構造体のカスタム コンス トラクター: 要求が失敗しました。** 
**新しい値 SecuredTypeStructure 100 100**
**SecuredTypeStructure 200 200 の新しい値**
## <a name="see-also"></a>関連項目
 [リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



