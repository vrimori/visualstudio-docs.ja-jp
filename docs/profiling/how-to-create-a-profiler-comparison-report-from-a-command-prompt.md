---
title: "方法: コマンド プロンプトからプロファイラー比較レポートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: コマンド プロンプトからプロファイラー比較レポートを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

2 つのプロファイル データ \(.VSP または .VSPS\) ファイルのパフォーマンス データを比較する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのレポートを生成できます。  このレポートには、プロファイル セッション間における相違点と、パフォーマンスの低下および向上が示されます。  レポート内の値は、最初に指定したファイルのベースラインからのデルタ \(変化\) を表します。  このデルタは、古い値 \(ベースライン値\) と、新しい分析に基づく結果値の差異を測定することによって計算されます。  プロファイラー データの比較は、コード内の関数、アプリケーション モジュール、行、命令ポインター \(IP\)、およびデータ型に基づいて行われます。  
  
 比較のカテゴリおよびフィールドの識別子を一覧表示するには、次のコマンド ラインを入力します。  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 比較レポートを作成するには、次の構文を使用します。  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 **VSPerfReport \/diff** コマンド ラインには、次の表のオプションを追加できます。  
  
|オプション|説明|  
|-----------|--------|  
|**DiffThreshold:**\[*Value*\]|このパーセントしきい値未満の値の場合、差異を無視します。  また、このしきい値未満の値を持つ新規データは表示されません。|  
|**DiffTable:** *TableName*|このテーブルを使用してファイルを比較します。  既定では、関数テーブルが使用されます。  **VSPerfReport \/querydifftables** で一覧表示される識別子を指定します。|  
|**DiffColumn:** *ColumnName*|この列を使用して値を比較します。  既定では、排他サンプルのパーセント列が使用されます。  **VSPerfReport \/querydifftables** で一覧表示される識別子を指定します。|