---
title: ISimpleConnectionPoint::Advise |Microsoft ドキュメント
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
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733792"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
単純な接続ポイント オブジェクトとクライアントのシンク間の接続を確立します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdisp`  
 [in]ポインター、`IDispatch`クライアント上のインターフェイスのシンクをお勧めします。 クライアントのシンクは、単純な接続ポイントから送信呼び出しを受信します。  
  
 `pdwCookie`  
 [out]この接続を一意に識別する返されたトークンへのポインター。 呼び出し元は、このトークンを使用して後でに渡すことによって、接続を削除、`ISimpleConnectionPoint::Unadvise`メソッドです。 接続が正常に確立されなかった場合、この値は 0 を使用します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、単純な接続ポイント オブジェクトとクライアントのシンク間の接続を確立します。  
  
## <a name="see-also"></a>関連項目  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)