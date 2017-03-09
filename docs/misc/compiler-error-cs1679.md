---
title: "コンパイラ エラー CS1679 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1679
'\/reference' の extern エイリアスが正しくありません。'identifier' は正しい識別子ではありません  
  
 **\/reference** オプションの外部アセンブリのエイリアス機能を使用する場合、**\/reference:** の後に続き '\=' の前にあるテキストは、正しい C\# 識別子であるか、C\# 言語仕様に従ったキーワードでなければなりません。  
  
 このエラーを解決するには、"\=" の前のテキストを正しい C\# 識別子かキーワードに変更します。  
  
## 使用例  
 次の例では CS1679 が生成されます。  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```