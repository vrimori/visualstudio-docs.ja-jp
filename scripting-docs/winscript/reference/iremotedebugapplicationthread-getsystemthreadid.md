---
title: IRemoteDebugApplicationThread::GetSystemThreadId |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSystemThreadId
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSystemThreadId
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0082382c5a9d6dc854ed1b7bc9f45b17041b8084
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728782"
---
# <a name="iremotedebugapplicationthreadgetsystemthreadid"></a>IRemoteDebugApplicationThread::GetSystemThreadId
スレッドに関連付けられているオペレーティング システム依存識別子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwThreadId`  
 [out]スレッドに関連付けられているオペレーティング システム依存の識別子です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 値`dwThreadId`するマシン間で一意である必要はありません。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)