---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
各参照には、次のように、関連付けられた **Name** プロパティが必要です。  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 このエラーは、1 つ以上の参照に **Name** プロパティが見つからないことを示します。  
  
 このエラーの原因として最も可能性が高いのは、プロジェクト ファイルを手動で編集したことです。  
  
 **このエラーを解決するには**  
  
-   参照を再度追加します。  
  
     影響を受けた参照は、プロジェクトには追加されません。  
  
## 参照  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)