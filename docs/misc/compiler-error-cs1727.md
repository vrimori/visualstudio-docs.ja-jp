---
title: "コンパイラ エラー CS1727 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1727"
ms.assetid: 66478a58-e0f6-4886-b940-5473ad485a01
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1727
承認なしにエラー報告を自動的に送信することはできません。 エラー報告送信の承認を受けるには、'' にアクセスしてください。  
  
 エラー テキストに示されている Web サイトでは、[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] コマンド ライン ツールに対して自動エラー報告を有効にする方法について説明しています。  
  
## 使用例  
 次の例では CS1727 が生成されます。  
  
```  
// CS1727.cs // compile with: /errorreport:send // CS1727 expected class Test { static void Main(){} }  
```  
  
## 参照  
 [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)