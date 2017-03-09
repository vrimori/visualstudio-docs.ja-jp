---
title: "&#39;#End Region&#39; の前には、対応する &#39;#Region&#39; を指定しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; の前には、対応する &#39;#Region&#39; を指定しなければなりません
`#Region` では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コード エディターのアウトライン機能を使用して、展開または折りたたみの対象となるコード ブロックを指定できます。`#Region` ステートメントの開始と終了は同じコード ブロック内にある必要があります。  
  
 **エラー ID:** BC30680  
  
### このエラーを解決するには  
  
-   `#Region` を適切な場所に挿入してから、対応する `#End` `Region` ステートメントを配置します。  
  
## 参照  
 [\#Region Directive](/dotnet/visual-basic/language-reference/directives/region-directive)