---
title: "2124: 脆弱なラップ finally 句外側の try |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f4d30a07ed0930d5165629f7c4b468d7e5146613
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: 脆弱性のある finally 句の外側を try ブロックでラップします
|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 バージョン 1.0 および 1.1 では、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、パブリックまたはプロテクト メソッドが含まれています、 `try` / `catch` / `finally`ブロックします。 `finally`ブロックがセキュリティ状態をリセットするが表示されで囲まれていない、`finally`ブロックします。  
  
## <a name="rule-description"></a>規則の説明  
 このルールを検索`try` / `finally`の version 1.0 および 1.1 を対象とするコード内のブロック、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]コール スタック内にある悪意のある例外フィルターを受ける可能性があります。 前に、フィルターが実行される偽装などの機密性の高い操作は、try ブロックで発生する、例外がスローされると場合、`finally`ブロックします。 権限借用例では、フィルターが権限を借用したユーザーとして実行されていることを意味します。 フィルターは、Visual Basic でのみ実装されています。  
  
> [!WARNING]
>  **注**2.0 以降のバージョンでは、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、ランタイムが自動的に保護、 `try` / `catch` /  `finally`リセットが発生した場合、悪意のある例外フィルター ブロックメソッド内で直接例外ブロックを含むです。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 配置、ラップされていない`try` / `finally` try ブロックの外側にします。 次の 2 番目の例を参照してください。 これにより、`finally`フィルター コードの前に実行します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="pseudo-code-example"></a>擬似コードの例  
  
### <a name="description"></a>説明  
 次の擬似コードでは、このルールにより検出されたパターンを示しています。  
  
### <a name="code"></a>コード  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## <a name="example"></a>例  
 次の擬似コードでは、コードを保護して、この規則を満たすために使用できるパターンを示します。  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```