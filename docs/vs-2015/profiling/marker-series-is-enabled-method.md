---
title: marker_series::is_enabled メソッド | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db5a91a3b2212967cb1de915f15abb9d5caa9d98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537557"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled メソッド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[marker_series::is_enabled メソッド](https://docs.microsoft.com/visualstudio/profiling/marker-series-is-enabled-method)します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [marker_series クラス](../profiling/marker-series-class.md)



