---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60db5058f3a084a4d24f3b3a1d83e615a9071d8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920255"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
現在のコンテキストの追跡を終了します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>戻り値  
 コンテキストの追跡が終了した場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:***FileTracker.h*  
  
## <a name="see-also"></a>関連項目  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)