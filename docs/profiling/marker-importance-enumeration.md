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
ms.openlocfilehash: 6541ddecceff6d9e7867dd5feead3457b2248b45
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844119"
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
 **ヘッダー:** *cvmarkersobj.h*  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>関連項目  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)