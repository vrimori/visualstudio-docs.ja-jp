---
title: "The property &lt;property name&gt; cannot be deleted | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The property &lt;property name&gt; cannot be deleted
プロパティ \<property name\> は、\<class name\> と \<class name\> との間の継承に対する識別子のプロパティとして設定されているため、削除できません。  
  
 選択されたプロパティは、エラー メッセージに示されているクラス間の継承に対する**識別子のプロパティ**として設定されています。プロパティがデータ クラス間の継承構成に関与している場合、そのプロパティを削除することはできません。  
  
 **識別子のプロパティ**をデータ クラスの別のプロパティに設定して、目的のプロパティが正常に削除されるようにしてください。  
  
### このエラーを解決するには  
  
1.  O\/R デザイナーで、エラー メッセージに示されているデータ クラスを接続する継承線を選択します。  
  
2.  **識別子**プロパティを別のプロパティに設定します。  
  
3.  プロパティの削除を再試行します。  
  
## 参照  
 [How to: Configure Inheritance by Using the O\/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Data Class Inheritance \(O\/R Designer\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)