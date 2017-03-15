---
title: "コンパイラの警告 (レベル 1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0626
メソッド、演算子、またはアクセサー 'method' が外部としてマークされているが、属性が設定されていません。 外部の実装を指定するには、DllImport 属性を追加してください。  
  
 `extern` としてマークされているメソッドは、[DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic) 属性などの属性でもマークされる必要があります。  
  
 属性は、メソッドを実装する場所を指定します。 実行時、プログラムにこの情報が必要になります。  
  
 次の例では CS0626 が生成されます。  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```