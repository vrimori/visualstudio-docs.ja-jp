---
title: "このプロジェクトでは、同じパラメーター値を使用する場合でも、属性 &#39;&lt;attributename&gt;&#39; を 2 回以上指定することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# このプロジェクトでは、同じパラメーター値を使用する場合でも、属性 &#39;&lt;attributename&gt;&#39; を 2 回以上指定することはできません
カスタム属性を同じプログラミング要素に複数回指定していますが、<xref:System.AttributeUsageAttribute> をカスタム属性に適用し、その <xref:System.AttributeUsageAttribute.AllowMultiple%2A> プロパティを `False` に設定しています。<xref:System.AttributeUsageAttribute.AllowMultiple%2A> は、属性を複数回使用するかどうかを制御します。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC41000  
  
### このエラーを解決するには  
  
-   カスタム属性の余分な仕様を削除するか、またはカスタム属性に適用している <xref:System.AttributeUsageAttribute> で <xref:System.AttributeUsageAttribute.AllowMultiple%2A> を `True` に設定します。  
  
## 参照  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)