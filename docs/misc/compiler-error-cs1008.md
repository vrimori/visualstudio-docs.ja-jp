---
title: "コンパイラ エラー CS1008 | Microsoft Docs"
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
  - "CS1008"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1008"
ms.assetid: e595a431-2cf0-4cc1-998f-94aecb2a6db1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1008
byte、sbyte、short、ushort、int、uint、long または ulong のいずれかの型を使用してください。  
  
 [列挙型](/dotnet/csharp/language-reference/keywords/enum)などの特定のデータ型は、指定された型のデータを保持するためにのみ宣言できます。  
  
 次の例では CS1008 が生成されます。  
  
```  
// CS1008.cs abstract public class clx { enum splitch : char   // CS1008, char not valid type for enums { x, y, z } public static void Main() { } }  
```