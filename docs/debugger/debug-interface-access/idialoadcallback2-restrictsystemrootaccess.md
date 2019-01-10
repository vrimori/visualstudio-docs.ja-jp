---
title: Idialoadcallback 2::restrictsystemrootaccess |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340e6a8cffbf681bb9e976664ccbbe15e6b00786
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918734"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
システム ルート ディレクトリで .pdb ファイルの検索を許可するかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのコード以外のリターン`S_OK`.pdb ファイルのシステム ルートを検索できないようにします。  
  
## <a name="see-also"></a>「  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)