---
title: IRemoteDebugApplication::GetDebugger |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetDebugger
ms.assetid: 3d173b86-9281-4a3c-9550-d79408fd50ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 908d6b43ca33a3b9c35d2690ccb5453032ce151a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729192"
---
# <a name="iremotedebugapplicationgetdebugger"></a>IRemoteDebugApplication::GetDebugger
現在のデバッガーがアプリケーションに接続を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDebugger(  
   IApplicationDebugger**  pad  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pad`  
 [out]現在のデバッガーは、アプリケーションに接続します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、現在のデバッガーがアプリケーションに接続を返します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)   
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)