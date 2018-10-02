---
title: 'CA1506: クラス結合度の回避 |Microsoft Docs'
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
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2f96701ccecdd5e3859dcc434a748200f7fd784
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589059"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: クラス結合度を大きくしすぎないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1506: クラス結合度を避けるため](https://docs.microsoft.com/visualstudio/code-quality/ca1506-avoid-excessive-class-coupling)します。

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型またはメソッドは、さまざまな種類と結び付いています。

## <a name="rule-description"></a>規則の説明
 この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。

 型およびメソッドを持つクラス結合度の高度な保守が困難なできます。 型と結合度が低く、高い凝集度を示すメソッドを用意することをお勧めします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには結合されて型の数を減らすには、型またはメソッドを再設計してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 型またはメソッドと見なされます、大量の他の種類への依存関係があるにもかかわらず保守性の高いときに、この警告を除外します。

## <a name="see-also"></a>関連項目
 [保守性に関する警告](../code-quality/maintainability-warnings.md)[複雑さとマネージ コードの保守性を測定します。](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



