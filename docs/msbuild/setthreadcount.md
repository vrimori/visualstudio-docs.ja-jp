---
title: SetThreadCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13e7e2bb1ecabc67f60da7b2d4c68b413fa9cf92
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844367"
---
# <a name="setthreadcount"></a>SetThreadCount
グローバルなスレッド カウントを設定し、そのカウントを現在のスレッドに割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cmd  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>パラメーター  
 [入力] `threadCount`  
 使用するスレッドの数。  
  
## <a name="return-value"></a>戻り値  
 スレッド カウントが更新された場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:***FileTracker.h*