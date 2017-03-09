---
title: "ステートメントをインターフェイス本体内部に記述することはできません | Microsoft Docs"
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
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントをインターフェイス本体内部に記述することはできません
インターフェイス メンバーの宣言に、メンバーを終了するステートメントが `End` *membername* の形式で含まれています。  
  
 インターフェイスは、メンバーのシグネチャのみを定義します。 そのため、インターフェイスで定義されているプロシージャやプロパティには、名前とシグネチャを指定する最初の行しかありません。 インターフェイスの内部には、コード、内部宣言、または `End Function`、`End Property`、`End Sub` ステートメントを含めません。  
  
 **エラー ID:** BC30603  
  
### このエラーを解決するには  
  
-   インターフェイス定義から `End` *membername* ステートメントを削除します。  
  
## 参照  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)