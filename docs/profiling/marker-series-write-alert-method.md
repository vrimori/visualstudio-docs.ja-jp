---
title: marker_series::write_alert メソッド | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b41cd976ddd637faf00ee50a3ec208d2b3d513f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924942"
---
# <a name="markerserieswritealert-method"></a>marker_series::write_alert メソッド
コンカレンシー ビジュアライザーのトレース ファイルにアラートを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `_Format`  
 0 個以上の書式項目が混在したテキストを含む複合書式指定文字列。各書式項目は、引数リスト内のオブジェクトに対応します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** *cvmarkersobj.h*  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>関連項目  
 [marker_series クラス](../profiling/marker-series-class.md)