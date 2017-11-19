---
title: "IRemoteDebugApplicationThread::GetState |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
このスレッドの状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pState`  
 [out]次のスレッドの状態フラグの組み合わせです。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|スレッドが実行されています。|  
|THREAD_STATE_SUSPENDED|0x00000002|スレッドが中断されます。|  
|THREAD_BLOCKED|0x00000004|スレッドがブロックされます。|  
|THREAD_OUT_OF_CONTEXT|0x00000008|スレッドでは、コンテンツ外です。|  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、このスレッドの状態を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)