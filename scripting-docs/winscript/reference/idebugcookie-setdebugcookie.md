---
title: IDebugCookie::SetDebugCookie |Microsoft Docs
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
ms.openlocfilehash: d67ea7f4cc8a27364226a613c77d837f476c2530
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095044"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
アプリケーションのデバッグの cookie を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwDebugAppCookie`  
 [in]デバッグ アプリケーションを識別するクッキー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、1 つ以上のデバッガーをアタッチするプロセスは、デバッグのアプリケーションの cookie を設定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)