---
title: "埋め込み式の始めに &#39;%=&#39; が必要です | Microsoft Docs"
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
  - "vbc31179"
  - "bc31179"
helpviewer_keywords: 
  - "BC31179"
ms.assetid: 20b0382e-1744-47e4-84e1-7fc926cbc4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 埋め込み式の始めに &#39;%=&#39; が必要です
埋め込み式の始まりを示す識別子 `<%=` が正しくコード化されていません。 リテラル XML 要素の名前には、パーセント文字 \(%\) を使用できないことに注意してください。  
  
 **エラー ID:** BC31179  
  
### このエラーを解決するには  
  
-   埋め込み式の始まりを示す識別子が `<%=` としてコード化されていることを確認します。  
  
## 参照  
 [Embedded Expressions in XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)