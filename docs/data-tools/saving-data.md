---
title: "データの保存 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.RowState"
  - "DataSet.GetChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 保存"
  - "データ [Visual Studio], 更新"
  - "データベース, 更新"
  - "DBDirect メソッド"
  - "保存 (データを)"
  - "TableAdapter DBDirect メソッド"
  - "TableAdapter.Update メソッド"
  - "更新 (データを)"
  - "更新 (データベースを)"
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# データの保存
データ保存は、アプリケーションのデータ モデルで変更されたデータを元のデータ ストア \(通常は SQL Server などのリレーショナル データベース\) に戻して保持するプロセスです。  
  
 データ モデルを介してデータ ソースを更新するには、2 段階のプロセスがあります。  第 1 段階のプロセスは、新しい情報 \(新しいレコード、変更されたレコード、または削除されたレコード\) によるデータ モデルの更新です。  第 2 段階のプロセスは、データ モデルの変更をデータベースに保存することです。  
  
 次のトピックでは、データの保存に関連する概念とタスクについて説明します。  
  
## 関連トピック  
 [データセットのデータの保存](../data-tools/save-data-back-to-the-database.md)  
 データセットで変更を加える方法と、データベースに変更内容を保存するためにデータセットが情報を追跡する方法の概要について説明します。  
  
 [エンティティ データの保存](../data-tools/saving-entity-data.md)  
 [ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md) アプリケーションおよび [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md) アプリケーションで変更を保存する方法について説明します。