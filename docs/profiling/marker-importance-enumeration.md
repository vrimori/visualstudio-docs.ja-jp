---
title: marker_importance 列挙型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f4c87cfa1504c997cefdc68416dac9923fa10b4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="markerimportance-enumeration"></a>marker_importance 列挙型
同時実行ビジュアライザー マーカーの重要度レベルを表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|name|説明|  
|----------|-----------------|  
|`critical_importance`|マーカーの重要度がきわめて高いことを指定します。|  
|`high_importance`|マーカーの重要度が高いことを指定します。|  
|`low_importance`|マーカーの重要度が低いことを指定します。|  
|`normal_importance`|マーカーの重要度が標準であることを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>参照  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)