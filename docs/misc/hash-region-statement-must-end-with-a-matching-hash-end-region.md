---
title: "&#39;#Region&#39; ステートメントの終わりには、対応する &#39;#End Region&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Region&#39; ステートメントの終わりには、対応する &#39;#End Region&#39; を指定しなければなりません
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コード エディターのアウトライン機能を使うときに展開または折りたたむことができるコード ブロックを指定するには、`#Region` ディレクティブを使用します。`#Region` ステートメントの開始と終了は同じコード ブロック内にある必要があります。  
  
 **エラー ID:** BC30681  
  
### このエラーを解決するには  
  
1.  コードの `#Region` ステートメントの後の適切な場所に `#End Region` を挿入します。  
  
## 参照  
 [\#Region Directive](/dotnet/visual-basic/language-reference/directives/region-directive)