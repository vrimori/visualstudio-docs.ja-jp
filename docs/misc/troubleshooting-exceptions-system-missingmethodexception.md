---
title: "例外のトラブルシューティング : System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "MissingMethodException クラス"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.MissingMethodException
存在しないメソッドに動的にアクセスしようとすると、<xref:System.MissingMethodException> 例外がスローされます。  
  
## 関連するヒント  
 **クラス ライブラリ内のメソッドを削除したり、名前を変更したりした場合は、そのメソッドを参照するすべてのアセンブリを再コンパイルします。**  
 通常、この例外は、厳密な名前で参照されない、削除または名前が変更されたアセンブリのメソッドに動的にアクセスしようとした場合にスローされます。  
  
## コメント  
 アンマネージ関数を呼び出しているときに、CLR がモジュールまたは関数を見つけることができない場合、この例外がスローされます。  
  
## 参照  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)