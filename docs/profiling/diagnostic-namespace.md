---
title: diagnostic 名前空間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3e6909bcb7299f4fd6d725334c26d2b59e0edb
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="diagnostic-namespace"></a>diagnostic 名前空間
`diagnostics` 名前空間は、同時実行ビジュアライザー マーカーを出力するための機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="classes"></a>クラス  
  
|name|説明|  
|----------|-----------------|  
|[marker_series クラス](../profiling/marker-series-class.md)|1 つのプロバイダーによって生成されたイベントのシリアル チャネルを表します。|  
|[span クラス](../profiling/span-class.md)|アプリケーションのフェーズを定義します。|  
  
### <a name="enumerations"></a>列挙  
  
|name|説明|  
|----------|-----------------|  
|[marker_importance 列挙型](../profiling/marker-importance-enumeration.md)|同時実行ビジュアライザー マーカーの重要度レベルを表します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency  
  
## <a name="see-also"></a>参照  
 [Concurrency 名前空間 (同時実行ビジュアライザー)](../profiling/concurrency-namespace-concurrency-visualizer.md)