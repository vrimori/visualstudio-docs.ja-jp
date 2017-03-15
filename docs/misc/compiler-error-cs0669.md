---
title: "コンパイラ エラー CS0669 | Microsoft Docs"
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
  - "CS0669"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0669"
ms.assetid: c7f81869-79d7-481f-a026-2cef0e87df4c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0669
ComImport 属性を持つクラスはユーザー定義のコンストラクターを持てません。  
  
 [ComImport](frlrfSystemRuntimeInteropServicesComImportAttributeClassTopic) クラスのコンストラクターは、共通言語ランタイムの COM 相互運用層に用意されています。 そのため、COM オブジェクトは、実行時にマネージ オブジェクトとして使用できます。  
  
 次の例では CS0669 が生成されます。  
  
```  
// CS0669.cs using System.Runtime.InteropServices; [ComImport, Guid("00000000-0000-0000-0000-000000000001")] class TestClass { TestClass()   // CS0669, delete constructor to resolve { } public static void Main() { } }  
```