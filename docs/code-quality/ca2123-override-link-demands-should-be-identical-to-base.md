---
title: "CA2123: オーバーライドのリンク要求をベースと同一にする必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3181e791d95f0268fd60654e8ceedb8fa394f7a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: オーバーライドのリンク確認要求は基本と同様にします
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリック型のパブリックまたはプロテクト メソッドがメソッドをオーバーライドまたはインターフェイスを実装し、同じではありません[リンク確認要求](/dotnet/framework/misc/link-demands)インターフェイスまたは仮想メソッドとして。  
  
## <a name="rule-description"></a>規則の説明  
 この規則は、メソッドをその基本メソッド (別の型のインターフェイスまたは仮想メソッド) とマッチングし、それぞれについてリンク確認要求を比較します。 メソッドまたは基本メソッドのいずれかのリンク確認要求があり、もう一方にない場合は、違反が報告されます。  
  
 この規則に違反する場合、悪意のある呼び出し元は、セキュリティ保護されていないメソッドを呼び出すだけで、リンク確認要求を省略することができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、オーバーライド メソッドや実装に同じリンク確認要求を適用します。 これが可能でない場合は、完全な demand でメソッドをマークまたは属性をすべて削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、このルールのさまざまな違反を示します。  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>参照  
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)   
 [リンク確認要求](/dotnet/framework/misc/link-demands)