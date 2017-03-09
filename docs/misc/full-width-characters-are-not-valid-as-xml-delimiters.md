---
title: "全角文字は、XML の区切り記号としては無効です | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 全角文字は、XML の区切り記号としては無効です
区切り記号として全角文字を含む、XML リテラルが定義されています。 全角文字はワイド文字またはマルチバイト文字とも呼ばれます。  
  
 **エラー ID:** BC31197  
  
### このエラーを解決するには  
  
-   XML リテラルの定義から全角文字を削除し、有効な ANSI 区切り文字に置き換えます。 有効な区切り記号の文字には `<`、`>`、`=`、`:`、`/` があります。  
  
## 参照  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [.NET Framework における文字エンコーディング](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)