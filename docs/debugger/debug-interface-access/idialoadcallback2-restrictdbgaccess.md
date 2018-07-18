---
title: Idialoadcallback 2::restrictdbgaccess |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b75db393822dc6c5d65bbbab4c9ccc64eed9f630
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459046"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
.Dbg ファイルからデバッグ情報を探すことが許可されたかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 戻り値以外の`S_OK`.dbg ファイルからデバッグ情報を探すことを防ぐためにします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)