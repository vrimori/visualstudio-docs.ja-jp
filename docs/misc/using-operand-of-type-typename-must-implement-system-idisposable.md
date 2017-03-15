---
title: "型 &#39;&lt;typename&gt;&#39; の &#39;Using&#39; オペランドは System.IDisposable を実装しなければなりません | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; の &#39;Using&#39; オペランドは System.IDisposable を実装しなければなりません
<xref:System.IDisposable> インターフェイスを実装しない型のリソースが `Using` ステートメントに指定されています。  
  
 `Using` ブロックの目的は、ブロックの終了時にシステム リソースを確実に廃棄することです。 この目的を満たすには、リソースは <xref:System.IDisposable> から実装された <xref:System.IDisposable.Dispose%2A> メソッドを公開する必要があります。  
  
 **エラー ID:** BC36010  
  
### このエラーを解決するには  
  
-   リソースを `Using` ステートメントのリソース リストから削除するか、<xref:System.IDisposable> を実装するリソースに置き換えます。  
  
## 参照  
 <xref:System.IDisposable>   
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)