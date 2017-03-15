---
title: "行連結文字 &#39;_&#39; は、その前に少なくとも 1 つの空白文字が必要で、また行の最後の文字でなければなりません | Microsoft Docs"
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
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 行連結文字 &#39;_&#39; は、その前に少なくとも 1 つの空白文字が必要で、また行の最後の文字でなければなりません
行連結文字、つまりアンダースコア \(\_\) を使用して、ファイルの複数行にわたる長いコード行を分割することができます。 アンダースコアは、スペースの直後、および行終端記号 \(キャリッジ リターン\) の直前に指定する必要があります。 例:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **エラー ID:** BC30999  
  
### このエラーを解決するには  
  
1.  行連結文字 \(\_\) がコード行の最後の文字であることを確認します。  
  
2.  行の他のコードから区切る行連結文字の前にスペースがあることを確認します。  
  
## 参照  
 [方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)