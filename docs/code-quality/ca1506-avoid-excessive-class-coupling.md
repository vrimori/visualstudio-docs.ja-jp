---
title: "CA1506: クラス結合度を避けるため |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5303e147ae001d887784aa401d456d23485c453
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: クラス結合度を大きくしすぎないでください
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|カテゴリ|Microsoft.Maintainability|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 型またはメソッドが他の多くの種類と結合されます。  
  
## <a name="rule-description"></a>規則の説明  
 この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。  
  
 型およびを大きなクラス結合度を持つメソッドが、維持するために難しい場合があります。 型とメソッドを抑え、連携性が高いことをお勧めします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この違反を修正するのには結び付いての種類の数を減らすには、型またはメソッドを再設計してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 型またはメソッドと見なされます、大量の他の種類の依存関係があるにもかかわらず保守しやすいときに、この警告を除外します。  
  
## <a name="see-also"></a>参照  
 [保守性に関する警告](../code-quality/maintainability-warnings.md)   
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)