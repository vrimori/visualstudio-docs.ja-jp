---
title: "既定のプロパティと &#39;|1&#39; 上で定義された &#39;DefaultMemberAttribute&#39; の間で競合が発生しました | Microsoft Docs"
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
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 既定のプロパティと &#39;|1&#39; 上で定義された &#39;DefaultMemberAttribute&#39; の間で競合が発生しました
クラス、構造体、またはインターフェイスは、[Default](/dotnet/visual-basic/language-reference/modifiers/default) キーワードを指定して既定のプロパティを宣言しますが、別のメンバーを既定のメンバーとして指定する <xref:System.Reflection.DefaultMemberAttribute> も適用します。  
  
 型に指定できる既定のメンバーは 1 つまでです。 既定のプロパティを宣言すると、Visual Basic は、そのプロパティを指定するクラス、構造体、またはインターフェイスに <xref:System.Reflection.DefaultMemberAttribute> を自動的に適用します。  
  
 **エラー ID:** BC32304  
  
### このエラーを解決するには  
  
1.  どのメンバーをクラス、構造体、またはインターフェイスの既定のメンバーにするかを決定します。  
  
2.  競合している宣言 \(`Default` キーワードまたは <xref:System.Reflection.DefaultMemberAttribute>\) を削除します。  
  
## 参照  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)   
 [ビルド内にありません: 既定のプロパティ](http://msdn.microsoft.com/ja-jp/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)