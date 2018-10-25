---
title: marker_series クラス | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a5791d338b204417d4d765b22a5050f4065faef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203859"
---
# <a name="markerseries-class"></a>marker_series クラス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

1 つのプロバイダーによって生成されたイベントのシリアル チャネルを表します。  
  
## <a name="syntax"></a>構文  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|名前|説明|  
|----------|-----------------|  
|[marker_series::marker_series コンストラクター](../profiling/marker-series-marker-series-constructor.md)|`marker_series` クラスの新しいインスタンスを初期化します。|  
|[marker_series::~marker_series デストラクター](../profiling/marker-series-tilde-marker-series-destructor.md)|marker_series オブジェクトを破棄し、すべての割り当て済みリソースを開放します。|  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[marker_series::is_enabled メソッド](../profiling/marker-series-is-enabled-method.md)|任意のセッションでプロバイダーが有効にされているかどうかを調べます。|  
|[marker_series::write_alert メソッド](../profiling/marker-series-write-alert-method.md)|コンカレンシー ビジュアライザーのトレース ファイルにアラートを書き込みます。|  
|[marker_series::write_flag メソッド](../profiling/marker-series-write-flag-method.md)|コンカレンシー ビジュアライザーのトレース ファイルにフラグを書き込みます。|  
|[marker_series::write_message メソッド](../profiling/marker-series-write-message-method.md)|コンカレンシー ビジュアライザーのトレース ファイルにメッセージを書き込みます。|  
  
## <a name="inheritance-hierarchy"></a>継承階層  
 `marker_series`  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>関連項目  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)



