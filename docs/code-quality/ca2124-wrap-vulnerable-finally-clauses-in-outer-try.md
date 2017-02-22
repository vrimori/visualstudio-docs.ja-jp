---
title: "CA2124: 脆弱性のある finally 句の外側を try ブロックでラップします | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124: 脆弱性のある finally 句の外側を try ブロックでラップします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョン 1.0 および 1.1 では、パブリック メソッドまたはプロテクト メソッドに `try`\/`catch`\/`finally` ブロックが含まれています。  セキュリティの状態をリセットすると見られる `finally` ブロックが `finally` ブロックに含まれていません。  
  
## 規則の説明  
 この規則は、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョン 1.0 および 1.1 を対象とするコードにおいて、コール スタックに悪意のある例外フィルターが存在する場合に、脆弱性が考えられる `try`\/`finally` ブロックの位置を特定します。  偽装など、注意が必要な操作が try ブロックで発生して例外がスローされると、`finally` ブロックの前にフィルターが実行される可能性があります。  たとえば偽装の場合、フィルターは偽装されたユーザーとして実行されます。  現在のところ、フィルターは Visual Basic でのみ実装できます。  
  
> [!WARNING]
>  **メモ**  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョン 2.0 以降では、例外ブロックが含まれるメソッド内で直接リセットが実行されると、ランタイムにより、悪意のある例外フィルターから `try`\/`catch`\/`finally` ブロックが自動的に保護されます。  
  
## 違反の修正方法  
 ラップされていない `try`\/`finally` の外側を try ブロックで囲みます。  以下の 2 つ目の例を参照してください。  これで、フィルター コードの前に `finally` が強制的に実行されます。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 擬似コードの例  
  
### 説明  
 次の擬似コードに、この規則で検出されるパターンを示します。  
  
### コード  
  
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
  
## 使用例  
 次の擬似コードに、コードを保護でき、この規則にも適合するパターンを示します。  
  
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