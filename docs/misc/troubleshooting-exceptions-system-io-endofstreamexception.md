---
title: "例外のトラブルシューティング : System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "EndOfStreamException クラス"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IO.EndOfStreamException
ストリームの末尾を超えて読み取ろうとすると、<xref:System.IO.EndOfStreamException> 例外がスローされます。  
  
## 関連するヒント  
 **読み取る前に、ファイルの終わりに達したかどうかを確認します。**  
 ストリームを読み取る前に、<xref:System.IO.StreamReader.Peek%2A> メソッドを使用してファイルの末尾を確認します。  
  
## 参照  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [方法 : ログ ファイルを開いて情報を追加する](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)