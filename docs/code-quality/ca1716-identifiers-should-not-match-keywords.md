---
title: "1716: 識別子はキーワードといない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 619fc7867d14a26f2c3b674b4b8ac8b2d8fba114
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: 識別子はキーワードと同一にすることはできません
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 名前空間、型、または viritual またはインターフェイス メンバーの名前では、プログラミング言語の予約されたキーワードと一致します。  
  
## <a name="rule-description"></a>規則の説明  
 識別子の名前空間、型、および仮想インターフェイスのメンバーが、共通言語ランタイムを対象とする言語で定義されているキーワードと一致する必要があります。 によって使用される言語とキーワードの場合は、コンパイラのエラーやあいまいさが困難ライブラリを使用します。  
  
 このルールは、次の言語のキーワードをチェックします。  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 大文字と小文字はため[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]キーワードと区別する比較は、その他の言語に使用します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 キーワードの一覧に表示されていない名前を選択します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制するには、識別子は、API のユーザーを混同しないことと、ライブラリが使用可能なすべての言語で使用可能であると確信している場合、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。