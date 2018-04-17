---
title: ': Ca 1823 使用されていないプライベート フィールド |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8af282866cd871d2717031091215cb431e1ec0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: 使用されていないプライベート フィールドを使用しません
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 このルールは、コード内のプライベート フィールドが存在しますが、任意のコード パスで使用されていない場合に報告されます。  
  
## <a name="rule-description"></a>規則の説明  
 アセンブリ内でアクセスされていないと思われるプライベート フィールドが検出されました。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、フィールドを削除するか、それを使用するコードを追加します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制しても安全です。  
  
## <a name="related-rules"></a>関連規則  
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)