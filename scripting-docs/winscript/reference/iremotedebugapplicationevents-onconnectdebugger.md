---
title: IRemoteDebugApplicationEvents::OnConnectDebugger |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnConnectDebugger
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnConnectDebugger
ms.assetid: 8c9c19b8-5426-4643-83e6-b68803ff69c4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ea40164dee8b4f7b82166ebc23abe1bc254226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728852"
---
# <a name="iremotedebugapplicationeventsonconnectdebugger"></a>IRemoteDebugApplicationEvents::OnConnectDebugger
デバッガー、ハンドルは、イベントを接続します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pad`  
 [in]新しく接続したデバッガーです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッガーを処理するイベントを接続します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)