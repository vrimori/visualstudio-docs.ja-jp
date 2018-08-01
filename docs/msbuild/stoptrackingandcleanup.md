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
ms.openlocfilehash: 1ffbebd651087d9aa877d0e257947352a0d0275e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154825"
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
 **ヘッダー:** *FileTracker.h*  
  
## <a name="see-also"></a>関連項目  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)