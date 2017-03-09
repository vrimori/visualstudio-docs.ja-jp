---
title: "例外のトラブルシューティング : System.Data.ConstraintException | Microsoft Docs"
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
  - "ConstraintException クラス"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Data.ConstraintException
制約に違反するアクションを試行すると、<xref:System.Data.ConstraintException> 例外がスローされます。  
  
## 関連するヒント  
 **データセットの制約を緩めるか、オフにします**。  
 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティを使用すると、<xref:System.Data.DataSet> オブジェクトのテーブルを読み込む間、一時的に制約をオフにできます。  
  
 **主キーが既にデータ テーブルに存在する場合に主キー フィールドに値を代入しようとしていないことを確認します。**  
 主キーが存在すると、この例外がスローされます。  
  
 **状態の表示から読み込む前に、データセットをクリアします。**  
 データセットを読み込むときにデータセットにデータが存在すると、この例外がスローされることがあります。  
  
## 参照  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)