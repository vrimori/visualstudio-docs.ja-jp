---
title: "CA2200: スタック詳細を保持するために再度スローします | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2200: スタック詳細を保持するために再度スローします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 例外が再スローされ、`throw` ステートメントで例外が明示的に指定されます。  
  
## 規則の説明  
 例外がスローされると、例外で伝達される情報の一部は、スタック トレースになります。  スタック トレースは、メソッドの呼び出し階層構造の一覧です。この一覧は、例外をスローするメソッドで始まり、例外をキャッチするメソッドで終了します。  `throw` ステートメントで例外を指定して例外が再スローされると、スタック トレースは現在のメソッドで再開され、例外をスローした元のメソッドと現在のメソッドの間で呼び出されたメソッドの一覧は失われます。  例外と共に元のスタック トレース情報を保存するには、例外を指定しないで `throw` ステートメントを使用します。  
  
## 違反の修正方法  
 この規則違反を修正するには、例外を明示的に指定せずに、例外を再スローします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反しているメソッド `CatchAndRethrowExplicitly` と、規則に適合するメソッド `CatchAndRethrowImplicitly` を次の例に示します。  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]