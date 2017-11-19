---
title: "IBindEventHandler::BindHandler |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66de7cba8181ce9f3d683a90e4d7dd51e63d4779
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
イベントをオブジェクトにバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrEvent`  
 [in]処理するイベントを指定します。  
  
 `pdisp`  
 [in]イベントを処理するオブジェクトを指定します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、イベントをオブジェクトにバインドします。  
  
## <a name="see-also"></a>関連項目  
 [IBindEventHandler インターフェイス](../../winscript/reference/ibindeventhandler-interface.md)