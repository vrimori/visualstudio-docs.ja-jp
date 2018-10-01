---
title: Idialoadcallback::restrictsymbolserveraccess |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 822fc19bac6223d0138176cf32c579b58871a85e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536653"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idialoadcallback::restrictsymbolserveraccess](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess)します。  
  
シンボルを解決するのには、シンボル サーバーへのアクセスが許可されたかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 すべてのコード以外のリターン`S_OK`シンボルを解決するシンボル サーバーを使用できないようにします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



