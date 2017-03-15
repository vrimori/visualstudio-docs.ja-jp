---
title: "イベント &#39;&lt;eventname&gt;&#39; の &#39;&lt;procedurename&gt;&#39; メソッドを包含する型 &#39;&lt;typename&gt;&#39; が CLS に準拠していないので、このメソッドを CLS 準拠としてマークすることはできません | Microsoft Docs"
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
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; の &#39;&lt;procedurename&gt;&#39; メソッドを包含する型 &#39;&lt;typename&gt;&#39; が CLS に準拠していないので、このメソッドを CLS 準拠としてマークすることはできません
カスタム イベントが `AddHandler` または `RemoveHandler` プロシージャを宣言し、`<CLSCompliant(True)>` としてマークしていますが、このイベントは `<CLSCompliant(False)>` としてマークされているか、マークされていない型で定義されています。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC40053  
  
### このエラーを解決するには  
  
-   CLS 準拠が必要な場合は、CLS に準拠している型の中でイベントを定義します。  
  
-   このイベントが、含んでいる型の中に保持される必要がある場合は、<xref:System.CLSCompliantAttribute> をその定義から削除するか、`<CLSCompliant(False)>` としてマークします。  
  
## 参照  
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [ビルド内にありません: AddHandler と RemoveHandler](http://msdn.microsoft.com/ja-jp/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)