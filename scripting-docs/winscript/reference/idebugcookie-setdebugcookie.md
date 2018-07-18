---
title: IDebugCookie::SetDebugCookie |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725822"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
デバッグ アプリケーションの cookie を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwDebugAppCookie`  
 [in]デバッグ アプリケーションを識別するクッキー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、1 つ以上のデバッガー プロセスにアタッチするのには、デバッグのアプリケーションの cookie を設定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)