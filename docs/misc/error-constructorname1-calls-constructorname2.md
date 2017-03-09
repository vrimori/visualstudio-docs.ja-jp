---
title: "&lt;error&gt;: &#39;&lt;constructorname1&gt;&#39; が &#39;&lt;constructorname2&gt;&#39; を呼び出しています | Microsoft Docs"
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
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;error&gt;: &#39;&lt;constructorname1&gt;&#39; が &#39;&lt;constructorname2&gt;&#39; を呼び出しています
コンストラクターの呼び出しが循環しています。 コンストラクターでは、`Me.New()` または `MyClass.New()` が呼び出されます。 異なる引数リストを持つ、オーバーロードされたコンストラクターを呼び出そうとしたことが、原因の 1 つとして考えられます。  
  
 **エラー ID:** BC30297  
  
### このエラーを解決するには  
  
-   異なる引数リストを使用して、オーバーロードされたコンストラクターを呼び出します。  
  
-   アクセス可能なオーバーロードされたコンストラクターがない場合は、`Me.New()` および `MyClass.New()` の呼び出しを削除します。  
  
## 参照  
 [NOT IN BUILD: コンストラクターとデストラクターの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)