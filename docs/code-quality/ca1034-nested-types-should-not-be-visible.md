---
title: "1034: 入れ子にされた型いないすることは表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc35514eab2344c086305ec88435ff8a32285e4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: 入れ子にされた型を参照可能にすることはできません
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 外部から参照できる型には、外部から参照できる型宣言が含まれています。 入れ子になった列挙体および保護されている型は、この規則から除外されます。  
  
## <a name="rule-description"></a>規則の説明  
 入れ子にされた型は、別の型のスコープ内で宣言された型です。 入れ子にされた型は、包含する型のプライベート実装の詳細をカプセル化するために役立ちます。 このような用途なので、入れ子にされた型は外部から参照できないようにします。  
  
 論理的なグループ化または名前の衝突を回避するために、外部から参照の入れ子にされた型を使用しません。代わりに、名前空間を使用します。  
  
 入れ子にされた型には、メンバーのアクセシビリティは、プログラマによってを明確に理解していないという概念が含まれます。  
  
 Protected 型は、サブクラスを高度なカスタマイズ シナリオで入れ子にされた型で使用できます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 外部から参照可能である入れ子にされた型をしない場合は、型のアクセシビリティを変更します。 それ以外の場合、入れ子にされた型を親から削除します。 入れ子の目的は、入れ子にされた型を分類するのには、代わりに、階層を作成するのに名前空間を使用します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例は、規則に違反する型を示しています。  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]