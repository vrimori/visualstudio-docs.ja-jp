---
title: "リソース コンパイラの警告 RC4204 | Microsoft Docs"
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
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# リソース コンパイラの警告 RC4204
仮想キー コードに相当しない ASCII 文字  
  
 VIRTKEY 型アクセラレータの仮想キー コードに文字列リテラルが使用されました。  
  
 この警告では、処理を続行できますが、生成されたアクセラレータ キーが指定した文字列と一致しない可能性があることに注意してください。 \(VIRTKEY は、ASCII アクセラレータとは異なるキー コードを使用します。\)  
  
 文字列リテラルは構文的に有効ですが、必要なアクセラレータを確実に入手できるのは、WINDOWS.h で **VK\_\*** `#define` を使用する場合のみです。