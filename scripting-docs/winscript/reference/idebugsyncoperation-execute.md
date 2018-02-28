---
title: "IDebugSyncOperation::Execute |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
同期的に、操作を実行し、返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppunkResult`  
 [out]操作によって返されるオブジェクトのパラメーターです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_ABORT`|呼び出して、操作が中止されました、`IDebugSyncOperation::InProgressAbort`メソッドです。|  
  
## <a name="remarks"></a>コメント  
 対象のスレッドの呼び出しでプロセスをデバッグ マネージャー、`Execute`メソッド同期的に処理します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)