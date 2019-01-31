---
title: marker_series::is_enabled メソッド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797953"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled メソッド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

任意のセッションでプロバイダーが有効にされているかどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `_Importance`  
 重要度レベル。  
  
 `_Category`  
 カテゴリ。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>「  
 [marker_series クラス](../profiling/marker-series-class.md)
