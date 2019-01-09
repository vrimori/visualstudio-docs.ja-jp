---
title: ISimpleConnectionPoint::Advise |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c0ea37e6fabb051458a11c4838061126bd98bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091742"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
単純な接続ポイント オブジェクトとクライアントのシンクの間の接続を確立します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdisp`  
 [in]ポインター、`IDispatch`クライアント上のインターフェイスのシンクをお勧めします。 クライアントのシンクは、単純な接続ポイントからの発信呼び出しを受信します。  
  
 `pdwCookie`  
 [out]この接続を一意に識別する返されたトークンへのポインター。 呼び出し元このトークンを使用して後でに渡すことによって、接続の削除、`ISimpleConnectionPoint::Unadvise`メソッド。 接続が正常に確立されませんが、この値は 0 です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、単純な接続ポイント オブジェクトとクライアントのシンクの間の接続を確立します。  
  
## <a name="see-also"></a>関連項目  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)