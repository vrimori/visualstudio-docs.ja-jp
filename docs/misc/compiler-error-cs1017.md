---
title: "コンパイラ エラー CS1017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1017
catch 句を、try ステートメントの一般的な catch 句の後に置くことはできません。  
  
 パラメーターを一切受け取らない `catch` ブロックは、一連の `catch` ブロックの最後に配置する必要があります。 例外の詳細については、「[例外処理ステートメント](/dotnet/csharp/language-reference/keywords/exception-handling-statements)」を参照してください。  
  
## 使用例  
 次の例では CS1017 が生成されます。  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```