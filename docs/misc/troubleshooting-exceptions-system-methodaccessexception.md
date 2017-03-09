---
title: "例外のトラブルシューティング : System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException クラス"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.MethodAccessException
クラス内のプライベート メソッドやプロテクト メソッドへの無効なアクセスを試みると、<xref:System.MethodAccessException> 例外がスローされます。  
  
## 関連するヒント  
 **クラス ライブラリ内のメソッドのアクセス レベルを変更した場合は、クラス ライブラリを参照するすべてのアセンブリを再コンパイルします。**  
 通常、この例外は、呼び出し元がメンバーへのアクセス許可を持たない場合に発生します。  
  
## 参照  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)