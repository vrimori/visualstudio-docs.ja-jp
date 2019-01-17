---
title: Idialoadcallback 2::restrictreferencepathaccess |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 121b5a4c74fd017e39314de7afe760a8d6184e25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872136"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
.Exe ファイルが配置されるパスで .pdb ファイルを検索が許可されているかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictReferencePathAccess();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのコード以外のリターン`S_OK`.exe ファイルの場所のパスで .pdb ファイルを検索しないようにします。  
  
## <a name="see-also"></a>「  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)