---
title: "コンパイラの警告 (レベル 1) CS1694 | Microsoft Docs"
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
  - "CS1694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1694"
ms.assetid: 9cb6b5d4-36a0-4b07-9690-14b5105da44b
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1694
プリプロセッサ ディレクティブに対して無効なファイル名が指定されました。 ファイル名が長すぎるか、有効なファイル名ではありません。  
  
 この警告は `#pragma checksum` プリプロセッサ ディレクティブを使用した場合に発生します。 指定したファイル名が 256 文字を超えています。 この警告を解決するには、短いファイル名を使用します。  
  
## 使用例  
 次の例では CS1694 が生成されます。  
  
```  
// cs1694.cs #pragma checksum "MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890.txt" {00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F}   // CS1694 class MyClass {}  
```