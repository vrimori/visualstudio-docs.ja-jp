---
title: CvLeaveSpan 関数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe234d60e8cd86279d3dcc01da95e6d2e6202213
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749159"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan 関数
スパンの終了を示します。  
  
## <a name="syntax"></a>構文  
  
```C  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSpan`  
 CvEnterSpan* を以前に呼び出したときに返されたスパン オブジェクト。 Nll は指定できません。  
  
## <a name="return-value"></a>戻り値  
 メッセージが書き込まれると S_OK を返します。 エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** *cvmarkers.h*  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)