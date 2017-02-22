---
title: "方法: プロファイリング ツールのコール トレース レポートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio ALM], 表示 (データを)"
  - "パフォーマンス ツール, 表示 (ETW データを)"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: プロファイリング ツールのコール トレース レポートを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールの*コール トレース レポート*は、アプリケーションの関数に対する各エントリ ポイントと終了ポイント、および実行中の関数から他の関数に対する各呼び出しのタイミング情報を一覧表示します。  コール トレース レポートをデータのプロファイリングに使用できるのは、インストルメンテーション メソッドで収集された場合だけです。  
  
> [!NOTE]
>  コール トレース レポートを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で表示することはできません。  コンマ区切り値 \(.csv\) ファイルまたは XML ファイルを生成するには、**VSPerfReport** のコマンド ライン ツールを使用する必要があります。  このツールの詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
### コール トレース レポートを作成するには  
  
1.  **\[コマンド プロンプト\]** ウィンドウを開きます。  
  
2.  コマンド プロンプトに次のコマンドを入力します。  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|プロファイリング ツールのコマンド ライン ツールのパス。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。|  
    |*VSPFile*|プロファイル データ \(.vsp または .vsps\) ファイル。  完全パスまたは部分パスで指定できます。|  
    |Xml|XML 形式のレポートを生成します。|  
  
## 参照  
 [方法: ETW \(Event Tracing for Windows\) データを収集する](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [プロファイリング ツールの API](../profiling/profiling-tools-apis.md)