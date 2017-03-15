---
title: "&#39;NotInheritable&#39; クラスに、&#39;&lt;specifiername&gt;&#39; として宣言されたメンバーを指定することはできません | Microsoft Docs"
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
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotInheritable&#39; クラスに、&#39;&lt;specifiername&gt;&#39; として宣言されたメンバーを指定することはできません
オーバーライド修飾子は `NotInheritable` クラスと一緒に使用できません。このクラスのメンバーはオーバーライドできないためです。  
  
 **エラー ID:** BC30607  
  
### このエラーを解決するには  
  
-   `Overridable`、`NotOverridable`、`MustOverride`、などのオーバーライド修飾子をクラス定義から削除します。  
  
## 参照  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)