---
title: "呼び出し式またはインデックス式が無効です | Microsoft Docs"
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
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 呼び出し式またはインデックス式が無効です
プロシージャ、プロパティ、配列でない式の後ろに、かっこで囲んだ値を指定しています。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 `Nothing` は引数やインデックスを取らないので、かっこで囲んだ値を指定できません。  
  
 **エラー ID:** BC32303  
  
### このエラーを解決するには  
  
-   かっことその中の値を削除します。  
  
## 参照  
 [How to: Call a Procedure That Returns a Value](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [How to: Call a Procedure that Does Not Return a Value](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [ビルド内にありません: 方法: 配列に値を格納する](http://msdn.microsoft.com/ja-jp/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [ビルド内にありません: 方法: 配列から値を取得する](http://msdn.microsoft.com/ja-jp/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [How to: Put a Value in a Property](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [How to: Get a Value from a Property](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)