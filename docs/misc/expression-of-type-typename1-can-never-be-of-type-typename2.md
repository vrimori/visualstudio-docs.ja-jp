---
title: "型 &#39;&lt;typename1&gt;&#39; の式を型 &#39;&lt;typename2&gt;&#39; にすることはできません | Microsoft Docs"
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
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename1&gt;&#39; の式を型 &#39;&lt;typename2&gt;&#39; にすることはできません
`TypeOf`...`Is` 式は、保持できないデータ型に対して、オブジェクト参照変数をテストします。  
  
 場合によっては、コンパイラによって `TypeOf`...`Is` テストが常に失敗する可能性があると判別されることがあります。たとえば、2 つのクラス間に継承関係がない場合などです。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 <xref:System.Windows.Forms.Form> と <xref:System.Array> はまったく関係のない型なので、コンパイラは `TypeOf`...`Is` 式が `refVar` の任意の値に対して `False` を返すことを判別できます。  
  
 **エラー ID:** BC31430  
  
### このエラーを解決するには  
  
-   現実的なデータ型の変数をテストするか、または `TypeOf`...`Is` テストをすべて削除します。  
  
## 参照  
 [TypeOf Operator](/dotnet/visual-basic/language-reference/operators/typeof-operator)   
 [How to: Determine What Type an Object Variable Refers To](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)