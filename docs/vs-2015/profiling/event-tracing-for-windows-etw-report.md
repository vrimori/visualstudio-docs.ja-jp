---
title: Event Tracing for Windows (ETW) レポート | Microsoft Docs
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
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be86d9ad6243a91763778f7027252a78d6ef254
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724964"
---
# <a name="event-tracing-for-windows-etw-report"></a>ETW (Event Tracing for Windows) レポート
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows イベント トレーシング (ETW) レポートには、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイル ツールのパフォーマンス セッションで記録された ETW イベントが一覧表示されます。 ETW データはバイナリ (.etl) ファイルで収集されます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] インターフェイスでは ETW レポートを表示できません。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] インターフェイスのプロファイル ツールを利用して ETW データを収集する方法については、「[方法: ETW (Event Tracing for Windows) データを収集する](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)」を参照してください。  
  
-   [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールを利用して ETW データを収集する方法については、「[Events](../profiling/events-vsperfcmd.md)」を参照してください。  
  
-   ETW レポートは **VSReport/Summary:ETW** コマンドを利用して生成します。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
|Column|説明|  
|------------|-----------------|  
|**タイムスタンプ**|イベントが発生した日時を識別します。|  
|**プロセス ID**|イベントを生成したプロセスを識別します。|  
|**スレッド ID**|イベントを生成したスレッドを識別します。|  
|**説明**|イベント プロバイダーを識別します。|  
|**Type**|イベントの種類を識別します。|  
|**Properties**|イベントのプロパティ。 各イベントは角かっこで囲まれた名前と値のペアになり、コンマで区切られます。|



