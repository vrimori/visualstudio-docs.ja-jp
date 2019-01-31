---
title: パフォーマンス規則リファレンス | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b522f777be495392a39e5a89724fc5657be6ac95
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798434"
---
# <a name="performance-rules-reference"></a>パフォーマンス規則リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロファイリング ツールのパフォーマンス規則は、アプリケーションのパフォーマンスに関する追加の警告や情報を提供します。 パフォーマンス規則は、Windows やプロセッサのパフォーマンス カウンターなどのソースから収集されたプロファイリング実行のデータを分析します。 規則のメッセージは、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 統合開発環境のエラー出力ウィンドウに表示されます。 メッセージは、次のいずれかの規則レベルとして一覧表示されます。  
  
|||  
|-|-|  
|**エラー**|パフォーマンス上の問題の多くは明白なエラーではないため、エラー メッセージが生成される規則はわずかです。 エラー メッセージは、プロファイル データの収集の失敗を示す場合もあります。|  
|**警告**|警告は、パフォーマンス上の問題の原因となる可能性があるアプリケーションの領域、または最適化した方がよい可能性があるアプリケーションの領域を示します。|  
|**情報**|情報メッセージは、規則の条件の分析がエラー メッセージを生成するしきい値に達しなかったこと、またはメッセージの情報が有用ではあるがパフォーマンス上の問題を表していないことを示します。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ID 別のパフォーマンス規則](../profiling/performance-rules-by-id.md)  
  
 プロファイリング ツールのパフォーマンス規則は、次の 4 つのカテゴリに分類されます。  
  
|||  
|-|-|  
|[.NET Framework の使用に関するパフォーマンス規則](../profiling/dotnet-framework-usage-performance-rules.md)|.NET Framework を効率的に使用するのに役立つ規則。|  
|[メモリとページングのパフォーマンス規則](../profiling/memory-and-paging-performance-rules.md)|アプリケーションのマネージド メモリとページング動作を分析する規則。|  
|[プロファイリング ツールの使用に関する規則](../profiling/profiling-tools-usage-rules.md)|プロファイリング ツールを効率的に使用するのに役立つ規則。|  
|[リソース監視のパフォーマンス規則](../profiling/resource-monitoring-performance-rules.md)|プロファイリング実行のプロセッサとメモリの使用率に関する情報メッセージ。|
