---
title: "コンパイラ エラー CS0316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0316
パラメーター名 'name' は、自動的に生成されたパラメーター名と競合しています。  
  
 予約語は、パラメーター名として使用できません。 以下の例では、`value` は既定のプロパティまたはインデクサー アクセサーのコンテキストにおける予約語です。  
  
### このエラーを解決するには  
  
1.  パラメーターの名前を変更します。  
  
## 使用例  
 次のコードでは CS0316 が生成されます。  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## 参照  
 [インデクサー](/dotnet/csharp/programming-guide/indexers/index)   
 [C\# のキーワード](/dotnet/csharp/language-reference/keywords/index)