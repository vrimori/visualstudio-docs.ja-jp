---
title: "コンパイラ エラー CS0138 | Microsoft Docs"
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
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0138
using namespace ディレクティブは名前空間に対してのみ使用できます。'type' は名前空間ではなく型です。  
  
 [using](/dotnet/csharp/language-reference/keywords/using) ディレクティブでは、パラメーターとして名前空間の名前のみを使用できます。 詳細については、「[名前空間](/dotnet/csharp/programming-guide/namespaces/index)」を参照してください。  
  
 次の例では CS0138 が生成されます。  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```