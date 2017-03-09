---
title: "CLS 準拠の警告 CLS02409 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS02409
プロパティの getter メソッドおよび setter メソッドを実装するメソッドは、メタデータで SpecialName とマークします  
  
 プロパティの getter メソッドおよび setter メソッドを実装するメソッドは、メタデータで **specialname** を使用してマークされていません。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数の宣言では、CLS02409 の考えられる原因を示しています。  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 **specialname** キーワードを追加することで、この警告を解決することができます。  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```