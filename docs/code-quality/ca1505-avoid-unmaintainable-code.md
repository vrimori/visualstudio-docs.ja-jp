---
title: ": 1505 メンテナンスできないコード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: メンテナンスできないコードを使用しないでください
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|カテゴリ|Microsoft.Maintainability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 型またはメソッドの保守容易性指数が低い値です。  
  
## <a name="rule-description"></a>規則の説明  
 保守容易性指数は、次のメトリックを使用して計算されます。 コードの行数、プログラムのボリューム、サイクロマティック複雑度。 プログラムのボリュームは、型またはメソッドのコードにオペランドと演算子の数に基づいている理解の難易度の尺度です。 サイクロマティック複雑度は、型またはメソッドの構造上の複雑さの尺度です。 コード メトリックに関する詳細については、[複雑性の測定とマネージ コードの保守容易性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)です。  
  
 保守性の低いインデックスがあること示し型またはメソッド保守が困難な可能性がありますを再設計に適した候補になります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この違反を修正するには、型またはメソッドを設計し直す小さくより対象を絞った型またはメソッドに分割しようとします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 型またはメソッドと見なされます、大きなサイズに関係なく、または型またはメソッドを分割することはできません、保守性の高いときに、この警告を除外します。  
  
## <a name="see-also"></a>参照  
 [保守性に関する警告](../code-quality/maintainability-warnings.md)   
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)