---
title: "例外のトラブルシューティング : System.FieldAccessException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "FieldAccessException クラス"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.FieldAccessException
クラス内のプライベート フィールドやプロテクト フィールドへの無効なアクセスを試みると、<xref:System.FieldAccessException> 例外がスローされます。  
  
## 関連するヒント  
 **クラス ライブラリにあるフィールドのアクセス レベルが変更された場合、そのライブラリを参照するアセンブリを再コンパイルします。**  
 この例外は、通常、クラス ライブラリ内のフィールドのアクセス レベル \(`Public`、`Private` など\) を変更した後に、そのライブラリを参照する 1 つ以上のアセンブリを再コンパイルしていない場合にスローされます。  
  
## 参照  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)