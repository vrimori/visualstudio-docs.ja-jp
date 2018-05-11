---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 731e8091a91c49c8e17dbcd00c3aea32001115a0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
すべての追跡を停止し、追跡セッションで使用されているメモリを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>戻り値  
 追跡が停止された場合、**HRESULT** に **SUCCEEDED** ビットが設定され、返されます。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** FileTracker.h  
  
## <a name="see-also"></a>参照  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)