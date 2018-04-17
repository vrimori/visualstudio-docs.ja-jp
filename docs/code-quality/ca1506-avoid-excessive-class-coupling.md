---
title: 'CA1506: クラス結合度を避けるため |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 018abf05181be812bcf01fc9cb910745dc085bcf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>関連項目  
 [保守性に関する警告](../code-quality/maintainability-warnings.md)   
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)