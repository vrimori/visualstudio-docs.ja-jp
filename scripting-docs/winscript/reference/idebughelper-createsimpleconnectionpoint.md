---
title: IDebugHelper::CreateSimpleConnectionPoint |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcc598fa97d47a564ddb12aaa0480e42b6601118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727812"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
ラップするイベント インターフェイスを返します、指定された`IDispatch`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdisp`  
 [in]`IDispatch`ラップするオブジェクト。  
  
 `ppscp`  
 [out]イベント インターフェイスをラップする`pdisp`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 ラップするイベント インターフェイスを返します、指定された`IDispatch`(を参照してください[ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md))。  
  
## <a name="see-also"></a>関連項目  
 [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)