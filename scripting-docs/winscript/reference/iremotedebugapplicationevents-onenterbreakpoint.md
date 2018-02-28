---
title: "IRemoteDebugApplicationEvents::OnEnterBreakPoint |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnEnterBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnEnterBreakPoint
ms.assetid: e92a56a3-c462-4a76-8ae8-4b2e6836a711
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2d122f6b85853e488035615835b299173951953
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonenterbreakpoint"></a>IRemoteDebugApplicationEvents::OnEnterBreakPoint
ブレークポイントを入力するため、イベントを処理します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnEnterBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `prdat`  
 [in]ブレークポイントを入力した、アプリケーション スレッドです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ブレークポイントを入力するため、イベントを処理します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)