---
title: IDebugApplicationThread::SetStateString |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SetStateString
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SetStateString
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eafe5477759dbad109e5ae6294b477d56f9ee14
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726202"
---
# <a name="idebugapplicationthreadsetstatestring"></a>IDebugApplicationThread::SetStateString
スレッドの状態の説明を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrState`  
 [in]スレッドの状態の説明。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、スレッドの状態の説明を設定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)