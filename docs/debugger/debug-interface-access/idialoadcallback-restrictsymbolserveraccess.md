---
title: "Idialoadcallback::restrictsymbolserveraccess |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 05c79edf44b9a853917ade19d1616219ae2c1308
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
シンボルを解決するのには、シンボル サーバーのアクセスが許可されたかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのコード以外のリターン`S_OK`シンボルを解決するのには、シンボル サーバーを使用できないようにします。  
  
## <a name="see-also"></a>参照  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)