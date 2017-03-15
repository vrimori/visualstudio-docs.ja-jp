---
title: "データセットのリレーションシップ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データセット [Visual Basic], リレーションシップ"
  - "リレーションシップ, リレーションシップの概要"
  - "リレーションシップ, データセット"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# データセットのリレーションシップ
データセットには、リレーショナル データベースのような関連テーブルを格納できます。  データ テーブル間のリレーションシップを操作するオブジェクトが、**DataRelation** オブジェクトです。  次のトピックでは、ADO.NET の **DataRelation** オブジェクトの概要と、その作成方法、および **DataRelation** オブジェクトを使用して関連テーブル内のデータを操作する方法について説明しています。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## このセクションの内容  
 [DataRelation オブジェクトの概要](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 データセットでテーブル間のリレーションシップを指定する方法と、そのリレーションシップを利用する方法の概要を示します。  
  
 [方法 : データセット デザイナーで DataRelation を作成する](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 **データセット デザイナー**を使用してデータセットに <xref:System.Data.DataRelation> オブジェクトを追加する方法を説明します。  
  
 [方法 : 関連する DataTable のレコードにアクセスする](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 プログラムで、1 対多リレーションシップがあるテーブルを含む型指定されたデータセット内の関連レコードを返す方法を説明します。  
  
 [チュートリアル : データ テーブル間のリレーションシップの作成](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 **データセット デザイナー**を使用して 2 つのデータ テーブルを作成し、これらのテーブル間にリレーションシップを追加する方法を、段階ごとに説明します。  
  
## 関連項目  
 <xref:System.Data.DataRelation>  
 2 つの T:System.Data.DataTable オブジェクト間の親子のリレーションシップを表します。  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 T:System.Data.DataRow の子の行を取得します。  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 T:System.Data.DataRow の親の行を取得します。  
  
 <xref:System.Data.Rule>  
 <xref:System.Data.ForeignKeyConstraint> を適用した場合に実行されるアクションを示します。  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 列の各行内の値が一意である必要があるかどうかを示す値を取得または設定します。  
  
 <xref:System.Data.Constraint>  
 1 つ以上の <xref:System.Data.DataColumn> オブジェクトに適用できる制約を表します。  
  
## 関連項目  
 [DataRelation の追加](../Topic/Adding%20DataRelations.md)  
 <xref:System.Data.DataSet> のテーブル間のリレーションシップを作成する方法について説明します。  
  
 [DataRelation の移動](../Topic/Navigating%20DataRelations.md)  
 <xref:System.Data.DataSet> のテーブル間のリレーションシップを使用して、親子関係の子または親の行を戻す方法について説明します。  
  
 [DataRelation の入れ子化](../Topic/Nesting%20DataRelations.md)  
 <xref:System.Data.DataSet> の内容を XML データとして表現する場合における、入れ子になった <xref:System.Data.DataRelation> オブジェクトの重要性について説明します。また、入れ子になったこれらのオブジェクトの作成方法について説明します。