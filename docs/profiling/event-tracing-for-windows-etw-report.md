---
title: "ETW (Event Tracing for Windows) レポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW プロファイリング レポート"
  - "Windows イベント トレーシング プロファイリング レポート"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# ETW (Event Tracing for Windows) レポート
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows イベント トレーシング \(ETW\) レポート リスト [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロファイリング ツールのパフォーマンス セッションで記録された ETW イベント。  ETW データはバイナリ \(.etl\) ファイルに収集されます。  
  
> [!NOTE]
>  ETW レポートを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスに表示することはできません。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスからプロファイリング ツールを使用して ETW を収集する方法の詳細については、「[方法: ETW \(Event Tracing for Windows\) データを収集する](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)」を参照してください。  
  
-   [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールを使用して ETW データを収集する方法については、「[イベント](../profiling/events-vsperfcmd.md)」を参照してください。  
  
-   ETW レポートは、**VSReport \/Summary:ETW** コマンドを使用して生成します。  詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
|列|説明|  
|-------|--------|  
|**\[タイムスタンプ\]**|イベントが発生したタイミングを識別します。|  
|**プロセス ID**|イベントを生成したプロセスを識別します。|  
|**スレッド ID**|イベントを生成したスレッドを識別します。|  
|**説明**|イベント プロバイダーを識別します。|  
|**型**|イベントの種類を識別します。|  
|**プロパティ**|イベントのプロパティ。  各イベントは、コンマで区切られた名前と値のペアで、角かっこで囲まれます。|