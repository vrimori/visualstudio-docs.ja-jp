---
title: "diagnostic 名前空間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords: Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76d86738f53e0d6dc60289d1e3f395794f8482ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="diagnostic-namespace"></a>diagnostic 名前空間
`diagnostics` 名前空間は、同時実行ビジュアライザー マーカーを出力するための機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="classes"></a>クラス  
  
|名前|説明|  
|----------|-----------------|  
|[marker_series クラス](../profiling/marker-series-class.md)|1 つのプロバイダーによって生成されたイベントのシリアル チャネルを表します。|  
|[span クラス](../profiling/span-class.md)|アプリケーションのフェーズを定義します。|  
  
### <a name="enumerations"></a>列挙  
  
|名前|説明|  
|----------|-----------------|  
|[marker_importance 列挙型](../profiling/marker-importance-enumeration.md)|同時実行ビジュアライザー マーカーの重要度レベルを表します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency  
  
## <a name="see-also"></a>関連項目  
 [Concurrency 名前空間 (同時実行ビジュアライザー)](../profiling/concurrency-namespace-concurrency-visualizer.md)