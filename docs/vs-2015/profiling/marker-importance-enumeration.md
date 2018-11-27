---
title: marker_importance 列挙型 | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32e57a9463e6c6966c215066fd470b62596f5481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756857"
---
# <a name="markerimportance-enumeration"></a>marker_importance 列挙型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンカレンシー ビジュアライザー マーカーの重要度レベルを表します。  
  
## <a name="syntax"></a>構文  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|名前|説明|  
|----------|-----------------|  
|`critical_importance`|マーカーの重要度がきわめて高いことを指定します。|  
|`high_importance`|マーカーの重要度が高いことを指定します。|  
|`low_importance`|マーカーの重要度が低いことを指定します。|  
|`normal_importance`|マーカーの重要度が標準であることを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>関連項目  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)



