---
title: "方法: コマンド ラインからレポートをフィルター処理する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: コマンド ラインからレポートをフィルター処理する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfReport** コマンドのオプションを使用することで、プロファイル データ ファイルの特定の時間セグメントに合わせてレポートをフィルター処理したり、データを 1 つ以上のプロセスまたはスレッドに制限したりできます。  このコマンドの詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
|オプション|説明|  
|-----------|--------|  
|**StartTime:**\[*Value*\]|ミリ秒単位の時間 \(value\) よりも後に収集されたデータのみを表示します。|  
|**EndTime:**\[*Value*\]|ミリ秒単位の時間 \(value\) よりも前に収集されたデータのみを表示します。|  
|**FilterFile:** `VSPFFile`|Visual Studio の **\[パフォーマンス レポート\]** ウィンドウから生成されたフィルター ファイルの場所を指定します。|  
|**MsFilter:**\[*StartTime,Duration*\]|開始時刻 \(`StartTime`\) からミリ秒単位の時間 \(`Duration`\) 内のみのデータを表示します。|  
|**Process:**\[*Pid*\]|指定されたプロセスのデータのみを表示します。|  
|**Thread:**\[*ThreadID*\]|指定されたスレッドのデータのみを表示します。|  
|**Thread:**\[*ThreadID,ProcessID*\]|指定されたプロセスに関連付けられている指定されたスレッドのデータのみを表示します。|