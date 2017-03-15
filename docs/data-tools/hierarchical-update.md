---
title: "階層更新 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Basic], 階層更新"
  - "データセット [Visual Basic], 階層更新"
  - "階層更新"
  - "変更されたデータの保存"
  - "関連テーブル, 保存"
  - "保存 (データを), 変更されたデータ"
  - "保存 (データを), 階層更新"
  - "保存 (更新データを)"
  - "更新データの保存"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 階層更新
*階層更新*とは、参照整合性規則を保持しながら、複数の関連テーブルで構成されるデータセットから、更新されたデータをデータベースに保存するプロセスのことです。  *参照整合性*とは、関連レコードの挿入、更新、および削除を制御するデータベース内の制約によって定義される一貫性規則のことです。  たとえば、顧客レコードを先に作成しておかなければ、その顧客の注文を作成できないようにすることが参照整合性です。  
  
 関連付けられているデータ テーブルから変更されたデータの保存は、1 つのテーブルから変更されたデータの保存より若干複雑です。  これは、各関連テーブルの更新コマンド、挿入コマンド、および削除コマンドは、参照整合性制約に違反しない順序で実行する必要があるためです。  たとえば、新しい顧客と注文、および既存の顧客と注文の両方を管理できる注文入力アプリケーションがあるとします。  既存の顧客を削除する場合、顧客レコードを削除する前に、その顧客の注文をすべて削除しておく必要があります。  また、新しい顧客を注文と共に追加する場合は、テーブルに関連付けられている外部キー制約により、新しい顧客レコードを挿入してからでなければ、その顧客の注文を挿入することはできません。  これらの例が示すとおり、特定のデータのサブセットを抽出してから、参照整合性を維持する正しい順序で、更新 \(挿入コマンド、更新コマンド、および削除コマンド\) を送信する必要があります。  
  
 階層更新機能は、`TableAdapterManager` を使用して、型指定されたデータセットの `TableAdapter` を管理します。  `TableAdapterManager` コンポーネントは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって生成されるコンポーネントであり、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の一部ではありません。  `TableAdapterManager` クラスの詳細については、「[TableAdapterManager の概要](../Topic/TableAdapterManager%20Overview.md)」の TableAdapterManager の参照に関するセクションを参照してください。  
  
 アプリケーションが型指定されたデータセットを使用していて、関連データ テーブル \(Customers と Orders など、1 対多リレーションシップで関連付けられているデータ テーブル\) 内のデータをユーザーが変更できるようにするときは、多くの場合、階層更新を使用することになります。  
  
## このセクションの内容  
 [階層更新の概要](../Topic/Hierarchical%20Update%20Overview.md)  
 階層更新の概要および実装方法の詳細について説明します。  
  
 [TableAdapterManager の概要](../Topic/TableAdapterManager%20Overview.md)  
 `TableAdapterManager` の概要およびデータセット デザイナーによって生成される `TableAdapterManager` コードについて説明します。  
  
 [方法 : 階層更新を有効または無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 型指定されたデータセットの `Hierarchical Update` プロパティを設定して、関連テーブルを保存するためのコードを生成する方法について説明します。  
  
 [方法 : データセットでの外部キー制約を構成する](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 データセットの制約を構成する方法について説明します。  
  
 [方法 : データの保存前にデータ バインド コントロールで実行中の編集をコミットする](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 保存するデータ ソースを準備するためにフォーム上のデータ バインド コントロール内の実行中の編集をすべて停止する方法について説明します。  
  
 [方法 : 階層更新の実行順序を設定する](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 `TableAdapterManager` の `UpdateOrder` プロパティを設定して、挿入、更新、および削除を実行する順序を制御する方法について説明します。  
  
 [方法 : 既存の Visual Studio プロジェクトで階層更新を実装する](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 `TableAdapterManager` を使用して、関連データ テーブルにデータを保存するアプリケーションをアップグレードする方法について説明します。  
  
 [チュートリアル : 関連するデータ テーブルからのデータの保存 \(階層更新\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 関連データ テーブルを持つアプリケーションを作成し、`TableAdapterManager` を使用してデータを保存する方法の詳細な手順について説明します。  
  
## 関連項目  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## 関連項目  
 [n 層アプリケーションでのデータセットの操作](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [データの保存](../data-tools/saving-data.md)  
  
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapter](../Topic/TableAdapters.md)  
  
 [DataSets、DataTables、および DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTable](../Topic/DataTables.md)  
  
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)