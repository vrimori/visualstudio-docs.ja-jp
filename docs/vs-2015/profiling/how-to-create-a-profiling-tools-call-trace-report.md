---
title: '方法: プロファイリング ツールのコール トレース レポートを作成する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7699e169477dd0933532ff95a874d52dcf0e97d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775395"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>方法: プロファイリング ツールのコール トレース レポートを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールの*コール トレース レポート*は、アプリケーションの関数に対する各エントリ ポイントと終了ポイント、および実行中の関数から他の関数に対する各呼び出しのタイミング情報を一覧表示します。 コール トレース レポートをデータのプロファイリングに使用できるのは、インストルメンテーション メソッドで収集された場合だけです。  
  
> [!NOTE]
>  コール トレース レポートを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で表示することはできません。 コンマ区切り値 (.csv) ファイルまたは XML ファイルを生成するには、**VSPerfReport** のコマンド ライン ツールを使用する必要があります。 このツールの詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
### <a name="to-create-a-call-trace-report"></a>コール トレース レポートを作成するには  
  
1.  **[コマンド プロンプト]** ウィンドウを開きます。  
  
2.  コマンド プロンプトに次のコマンドを入力します。  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|プロファイリング ツールのコマンド ライン ツールのパス。 詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」をご覧ください。|  
    |*VSPFile*|プロファイル データ (.vsp または .vsps) ファイル。 完全パスまたは部分パスで指定できます。|  
    |Xml|XML 形式のレポートを生成します。|  
  
## <a name="see-also"></a>関連項目  
 [方法: ETW (Event Tracing for Windows) データを収集する](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [プロファイリング ツールの API](../profiling/profiling-tools-apis.md)



