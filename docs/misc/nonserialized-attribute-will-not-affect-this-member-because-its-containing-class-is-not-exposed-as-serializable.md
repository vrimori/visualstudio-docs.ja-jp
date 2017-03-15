---
title: "含まれるクラスが &#39;Serializable&#39; として公開されているため、&#39;NonSerialized&#39; 属性はこのメンバーに影響を与えません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 含まれるクラスが &#39;Serializable&#39; として公開されているため、&#39;NonSerialized&#39; 属性はこのメンバーに影響を与えません
既定では、クラスとそのメンバーはシリアル化不可能です。<xref:System.NonSerializedAttribute> 属性が必要になるのは、シリアル化可能なクラスのメンバーをシリアル化してはいけない場合だけです。  
  
 **エラー ID:** BC30772  
  
### このエラーを解決するには  
  
-   クラスに <xref:System.SerializableAttribute> 属性を追加します。  
  
     または  
  
-   メンバーから <xref:System.NonSerializedAttribute> 属性を削除します。  
  
## 参照  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)