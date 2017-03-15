---
title: "コンパイラ エラー CS1027 | Microsoft Docs"
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
  - "CS1027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1027"
ms.assetid: a6657f0f-5664-47a5-95cf-803f5a0e0c90
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1027
\#endif ディレクティブ が必要です。  
  
 指定された `#if` ディレクティブに、一致する `#endif` [プリプロセッサ ディレクティブ](/dotnet/csharp/language-reference/preprocessor-directives/index)が見つかりませんでした。 または、`#if` ブロック内に一致する `#region` ディレクティブがなかったときにコンパイラが `#endregion` ディレクティブを検出した可能性があります。  
  
 次の例では CS1027 が生成されます。  
  
```  
// CS1027.cs #if true   // CS1027, uncomment next line to resolve // #endif namespace x { public class clx { public static void Main() { } } }  
```