---
title: "&#39;DefaultEvent&#39; 属性で指定されたイベント &#39;&lt;eventname&gt;&#39; は、このクラスに対して公開されているアクセス可能なイベントではありません | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DefaultEvent&#39; 属性で指定されたイベント &#39;&lt;eventname&gt;&#39; は、このクラスに対して公開されているアクセス可能なイベントではありません
<xref:System.ComponentModel.DefaultEventAttribute> 属性では、属性を適用するクラスの、パブリックにアクセスできるイベントの名前を指定する必要があります。  
  
 **エラー ID:** BC30770  
  
### このエラーを解決するには  
  
1.  パブリックにアクセスできるイベントがクラスで定義されていることを確認します。  
  
2.  クラスのイベントの名前が、<xref:System.ComponentModel.DefaultEventAttribute> 属性で指定した名前と一致していることを確認します。  
  
## 参照  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)